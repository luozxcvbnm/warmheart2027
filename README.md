<!DOCTYPE html>
<html>
<head><meta charset="UTF-8"><title>暖心屿订阅</title></head>
<body>
    <h2>订阅成功！</h2>
    <p id="msg">正在发送确认通知...</p>
    <script>
        const openid = "你自己的OpenID";
        fetch("https://syunqggfglfbecwavjpl.supabase.co/functions/v1/send-wechat-template", {
            method: "POST",
            headers: { "Content-Type": "application/json" },
            body: JSON.stringify({
                openid: openid,
                type: "report",
                data: {
                    thing1: { value: "订阅确认" },
                    time2: { value: new Date().toLocaleString() },
                    thing3: { value: "您已成功订阅暖心屿每日提醒" }
                }
            })
        }).then(res => res.json()).then(data => {
            document.getElementById("msg").innerText = "通知已发送，请查看微信！";
        }).catch(err => {
            document.getElementById("msg").innerText = "发送失败：" + err.message;
        });
    </script>
</body>
</html>
