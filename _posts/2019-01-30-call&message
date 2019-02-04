---
title: "2018-01-30 Call & message"
date: 2018-01-30 08:26:28 -0400
---

1. 위급 상황이 발생했을 때 자동으로 911에 call하는 기능

<결과 화면>

![image](https://user-images.githubusercontent.com/32701768/52235697-e5f6be00-2892-11e9-9447-525d5af447b4.png)

<코드>
public void call() {
        Intent i = new Intent(Intent.ACTION_CALL, Uri.parse("tel:" + call_number));
        if (ActivityCompat.checkSelfPermission(mcontext, Manifest.permission.CALL_PHONE) != PackageManager.PERMISSION_GRANTED) {
            // TODO: Consider calling
            //    ActivityCompat#requestPermissions
            // here to request the missing permissions, and then overriding
            //   public void onRequestPermissionsResult(int requestCode, String[] permissions,
            //                                          int[] grantResults)
            // to handle the case where the user grants the permission. See the documentation
            // for ActivityCompat#requestPermissions for more details.
            return;
        }
        mcontext.startActivity(i);
    }
    
2. 위급 상황이 발생했을 때 db에 등록되어 있는 이웃에게 메시지를 보내는 기능

<결과 화면>

![image](https://user-images.githubusercontent.com/32701768/52235759-0888d700-2893-11e9-9006-bf06cde6a040.png)

<코드>
 public void sendMessage(int typeofemergency) {
        db = new Database(mcontext);
        sqLiteDatabase = db.getWritableDatabase();
        Cursor cursor = sqLiteDatabase.rawQuery("SELECT * FROM address", null);

        startManagingCursor(cursor);

        String message = "Neighbors are fall down!!! Please visit and call 911!!";
        while (cursor.moveToNext()) {
            if (typeofemergency == 1) {
                message = "[Fall Detection]\n"+message;
            } else if (typeofemergency == 2) {
                message = "[Heart Failure Detection]\n"+message;
            }
            try {
                SmsManager smsManager = SmsManager.getDefault();
                smsManager.sendTextMessage(cursor.getString(cursor.getColumnIndex("number")), null, message, null, null);
                Toast.makeText(mcontext, "Send Sucessful!", Toast.LENGTH_SHORT).show();
                message = "Neighbors are fall down!!! Please visit and call 911!!";
            } catch (Exception e) {
                Toast.makeText(mcontext, "SMS faile, please try again later!", Toast.LENGTH_LONG).show();
                e.printStackTrace();
            }
        }
    }

   

3. db에 이웃을 추가하는 기능

<결과 화면>

![image](https://user-images.githubusercontent.com/32701768/52235830-3b32cf80-2893-11e9-9110-54126a9a7d5b.png)

![image](https://user-images.githubusercontent.com/32701768/52235842-4128b080-2893-11e9-9957-e59563d67207.png)

<코드>

https://github.com/jakeoneijk/FiTec
(Database.java, PhonenumAdd.java, PhonenumberSave.java) 참조
