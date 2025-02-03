# Lecture Five

After reviewing the previous lecture, this session covers authentication and authorization. We’ll explore how to implement authentication and authorization in the front end, discuss browser storage options for saving data, and learn how to add data to request headers when making server requests.

## Lecture Five Materials and Links

- [Lecture Four](../Lesson-04/README.md)
- [Lecture Five Slides](Slides.md)
- [Lecture Five Recording]()
- [Code from Lecture Five]()
- [Lecture Six](../Lesson-06/README.md)
- [Zoom Link]()

### Topics

- [Authentication and Authorization](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Back-End-Frameworks/Topics/Auth/README.md)
- [Browser Storage Technologies](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Technologies/Topics/Browser-Memory/README.md)
- [JWT](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Back-End-Frameworks/Topics/JWT/README.md)
- [Sending Headers with Axios](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Technologies/Topics/Axios/README.md#sending-headers-with-axios)
- Implementing Authentication and Authorization

### Homework

Read the chapters covered in the lecture:

- [Authentication and Authorization](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Back-End-Frameworks/Topics/Auth/README.md)
- [Browser Storage Technologies](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Technologies/Topics/Browser-Memory/README.md)
- [JWT](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Back-End-Frameworks/Topics/JWT/README.md)
- [Sending Headers with Axios](https://github.com/FE-BE-Microdegrees/Subjects/tree/Front-end-Lessons/Front-End-Technologies/Topics/Axios/README.md#sending-headers-with-axios)

#### Assignment

Implement login functionality in your blog application and use `JWT` for making subsequent requests to the server:

- Add a form for user login with fields for email and password.
- Use Axios or another technology to send a request to the server.
- Store the `token` received in the server's response in the browser’s storage.
- Send requests to the server’s `/posts` endpoint, including the previously obtained `token` in the request headers.

