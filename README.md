SETUP

```
import nodemailer from "nodemailer";

export const sendMail = async (to, subject, text, html = "") => {
    try {
        const transporter = nodemailer.createTransport({
            host: "127.0.0.1", // Fake SMTP Server
            port: 8025, // Default Fake SMTP Port
            secure: false, // No SSL/TLS needed
        });

        const mailOptions = {
            from: "test@example.com",
            to,
            subject,
            text,
            html,
        };

        const info = await transporter.sendMail(mailOptions);
        console.log(`✅ Email Sent: ${info.messageId}`);
    } catch (error) {
        console.error("❌ Error Sending Email:", error.message);
    }
};
```


run commands

```
docker run -p 8025:8025 -p 8080:8080 gessnerfl/fake-smtp-server

sudo docker run -d --name fake-smtp -p 8025:8025 -p 8080:8080 gessnerfl/fake-smtp-server

```
