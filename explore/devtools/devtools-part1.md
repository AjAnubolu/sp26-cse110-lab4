# DevTools Part 1 - Network Tab

After clicking the "Fetch Data" button on the Lab 4 hosted site:

1. **What is the name of the new json file?**
   `citylots.json`

2. **Which file initiated the download of the new file?**
   `expose.js`

3. **What is the file size of the downloaded file?**
   `777,713 B` (~759 KB / ~760 KB)

4. **How long did it take to download?**
   ~1 second (varies based on network — observed roughly 900 ms in DevTools)

5. **What was your User-Agent for the browser that made the request?**
   `Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/120.0.0.0 Safari/537.36`

6. **In the response header, what type of server did it come from?**
   `GitHub.com`

7. **When was the file last modified?**
   `Tue, 21 Apr 2026 05:07:14 GMT`

8. **What was the Content-Type of the file?**
   `application/json; charset=utf-8`

9. **Which function inside the initiating file made the request?**
   `fetchData` (in `expose.js`) — it calls `fetch("citylots.json")` with `await`.
