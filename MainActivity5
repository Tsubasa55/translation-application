package com.websarva.wings.android.talksample2;

import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.os.Bundle;
import android.speech.tts.TextToSpeech;
import android.util.Log;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import java.util.Locale;

public class MainActivity5 extends AppCompatActivity  implements TextToSpeech.OnInitListener {

    TextToSpeech tts;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main5);

        tts = new TextToSpeech(this, this);
        Button btn = (Button) findViewById(R.id.action_read);
        btn.setOnClickListener(new View.OnClickListener() {
            public void onClick(View v) {
                if (v.getId() == R.id.action_read) {
                    speechText();
                }
            }
        });

        HelloListener listener = new HelloListener();

        Button btClear = findViewById(R.id.btClear);

        btClear.setOnClickListener(listener);
    }

    private static final int BT_CLEAR_BUTTON_ID = R.id.btClear;

    private class HelloListener implements View.OnClickListener {

        @Override
        public void onClick(View view) {

            EditText input = findViewById(R.id.etWord);

            TextView output = findViewById(R.id.etWord);

            int id = view.getId();

            if (id == BT_CLEAR_BUTTON_ID) {
                input.setText("");

                output.setText("");

            }
        }
    }

    @Override
    public void onInit(int status) {
        if (TextToSpeech.SUCCESS == status) {
            Locale locale = Locale.JAPAN;
            if (tts.isLanguageAvailable(locale) >= TextToSpeech.LANG_AVAILABLE) {
                tts.setLanguage(locale);
            } else {
                Log.d("Error", "Locale");
            }
        } else {
            Log.d("Error", "Init");
        }
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        if (null != tts) {
            tts.shutdown();
        }
    }

    private void speechText() {
        EditText editText = findViewById(R.id.etWord);
        String contents = editText.getText().toString();
        if (0 < contents.length()) {
            if (tts.isSpeaking()) {
                tts.stop();
            }
            System.out.println(contents);
            tts.speak(contents, TextToSpeech.QUEUE_FLUSH, null);
        }
    }

    public void onClick(View v) {
        Intent intent = new Intent(this, MainActivity.class);

        if (intent.resolveActivity(getPackageManager()) != null) {
            startActivity(intent);
        }
    }
}
