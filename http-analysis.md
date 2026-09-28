# HTTP Analysis

- **Website:** https://www.mos.org (Museum of Science, Boston)
- **Browser:** Google Chrome

## Request 1: HTML

- **Method:** GET
- **URL:** `https://www.mos.org/`
- **Status:** 200 OK
- **Response headers:**
    - `Age: 184192`: The age of the object in seconds as stored on a remote server.
    - `Content-Language: en`: This means that the intended audience for the content listed is English speakers.

## Request 2: CSS

- **Method:** GET
- **URL:** `https://www.mos.org/themes/custom/mos/dist/css/chunks/MultiSelect/MultiSelect-generated.css`
- **Status:** 200 OK
- **Response headers:**
    - `Age: 8259274`: The age of the object in seconds as stored on a remote server.
    - `Content-Length: 3796`: This means that the message body is exactly 3,796 bytes in size.

## Request 3: Image

- **Method:** GET
- **URL:** `https://www.mos.org/sites/default/files/mos-logo_0_2.png`
- **Status:** 200 OK
- **Response headers:**
    - `Age: 8259278`: The age of the object in seconds as stored on a remote server.
    - `Content-Length: 5873`: This means that the message body is exactly 5,873 bytes in size.

## Timing summary

- HTML: `89.08 ms`
- CSS: `49.88 ms`
- Image: `69.84 ms`

## Analysis

The HTML doc was the request that took the longest/was the slowest to load. Looking at the timing summary of the request, it stalled for `1.82 ms`, the dns lookup (Domain name -> IP) took `23.73 ms`, the initial connection and the ssl took `15.25 ms each`, the sending of the request took `0.21 ms`, the wait for the response from the server took `42.57 ms`, and finally the downloading of the content took `2.44 ms`. All of this means that the HTML page had to first make a secure connection to the server, and then ask for the server page to load after the connection was made. This connection and waiting for the response from the server took the longest time, causing the HTML doc to load the slowest.

For status codes, all of the codes read `200 OK`, which means that all of the requests were successfully received/understood. For some of the headers, I'll list the ones I've looked at. For `Age`, this means the age of the object, in seconds, as stored on a remote server. For `Content-Length`, this means that the message body of the request is X amount of bytes. Finally, for `Content-Language`, this means the intended language forthe audience to understand, for example `en` for English and `fr` for French.

One thing that had surprised me during this assignment was the CSS request stalled for so long before submitting it's request to the server. It stalled for `18.97 ms`, which is **38%** of the total time it took for the css file to load.
