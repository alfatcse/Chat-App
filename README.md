## View live demo: [www.chat-app.web.app](https://chat-app-client-egmb.onrender.com)
### ChatApp is an innovative chat application that leverages modern technologies such as Socket.io, React, React Bootstrap, HTML, CSS, and more to deliver a dynamic and interactive messaging experience. With its robust features and seamless integration, ChatApp allows users to connect, communicate, and express themselves in real-time with other users from around the world.
# Key Features🔑
 **User Authentication:** ChatApp provides a secure and reliable user authentication system, allowing users to create an account, log in, and safeguard their personal information. This ensures that only authorized users can access the chat application.
 
**Real-time Messaging:** With Socket.io, ChatApp enables real-time messaging capabilities, allowing users to send and receive messages instantly. Users can engage in one-on-one conversations fostering dynamic and interactive communication.

**Emoji Sharing:** ChatApp enhances communication by offering a wide range of emojis for users to express their emotions effectively. Users can easily select and share emojis within their messages, adding a personalized touch to their conversations.

**Responsive Design:** ChatApp incorporates React and Tailwind CSS framework to provide a responsive and visually appealing user interface. The application adapts seamlessly to different screen sizes and devices, ensuring a consistent user experience across platforms.

**Personalization Options:** ChatApp offers customization features, allowing users to personalize their chat experience. Users can customize their profiles, choose different themes or color schemes, and personalize their chat settings to suit their preferences.

---

# Demo :movie_camera:

![chattAppp (1)](https://github.com/alfatcse/Chat-App-Client/assets/34067640/f598ebc9-d0a8-40ad-a2d3-27d2f9af0722)

### Usage
* Run npm start:dev to start the application.
* Connect to the API using Postman on port 5009.
## Live Link:     [https://Chat-App-Server:4000](https://chat-app-server-414t.onrender.com)  
### API Endpoints
| HTTP Verbs | Endpoints | Action |
| --- | --- | --- |
| POST |api/v1/user/register | To Create new User |
| POST |api/v1/user/login | To Log in new user|
| POST |api/v1/setAvatar/:id | To set Avatar as profile picture|
| GET  |api/v1/allusers/:id | To get all the registered users|
| POST  |api/v1/addmsg | To send message any of the registered users|
| GET  |api/v1/getallmessages | To retrive all conversations of a specific user|
### Technologies Used
* [NodeJS](https://nodejs.org/) This is a cross-platform runtime environment built on Chrome's V8 JavaScript engine used in running JavaScript codes on the server. It allows for installation and managing of dependencies and communication with databases.
* [ExpressJS](https://www.expresjs.org/) This is a NodeJS web application framework.
* [MongoDB](https://www.mongodb.com/) This is a free open source NOSQL document database with scalability and flexibility. Data are stored in flexible JSON-like documents.
* [Socket.IO](https://socket.io/) Socket.IO is an event-driven library for real-time web applications. It enables real-time, bi-directional communication between web clients and servers. It consists of two components: a client, and a server. Both components have a nearly identical API.
* [Mongoose ODM](https://mongoosejs.com/) This makes it easy to write MongoDB validation by providing a straight-forward, schema-based solution to model to application data.
<hr>
### Sample Data: (User)

```json
{
     "username": "Müller",
     "email": "müller@gmail.com",
     "password": "12345678" 
     "avatarImage": "",
     "isAvatarImageSet": false
}
```
### Create a new User 
 Route:  api/v1/user/register (POST)
 
 Request body:
 ```json
 {
     "username": "Müller",
     "email": "müller@gmail.com",
     "password": "12345678" 
     "avatarImage": "",
     "isAvatarImageSet": false
}
```
 Response: The newly created user object.
 Response Sample Pattern:
```json
 {
      "status":"success" , 
      "message": "Data Inserted",
      "data": {
               "username": "Müller",
               "email": "müller@gmail.com",
               "password": "",//in hash format 
              "avatarImage": "",
             "isAvatarImageSet": false
              }, 
}
```        
### Login User

 Route:  api/v1/user/login (POST)
 
 Request body:
 ```json
  {
     "username": "Müller",
     "password": "12345678" 
  }
```
 Response: The user's array of objects.
 Response Sample Pattern:
```json
 {
      "status":"success" , 
      "message": "Data Retrived",
      "data": {
               "username": "Müller",
               "email": "müller@gmail.com",
               "password": "", //in hash format 
               "avatarImage":"PHuNTQx=PHN2ZyB4bmYwMDAwOyIvPjwvc3ZnPg===",
               "isAvatarImageSet": false
              }, 
}
```   

### Set avatar of a Single User

Route:  /api/v1/setAvatar/:id (POST)

Request Param: :id

 Request body:
 ```json
  {
     "_id": "" //id of the single user,
     "avatarImage": "PHuNTQx=PHN2ZyB4bmYwMDAwOyIvPjwvc3ZnPg===" 
  }
```

Response: The specified user object.

Response Sample Pattern:

```json
  {
      "success": "success", 
      "message": "Avatar Image set successfully",
  }
  ```  
  ### Get all Users

 Route:  /api/v1/allusers/:id (GET)
 
 Request Param: :id
 
 Response:  The array of all user object.
 
 Response Sample Pattern:
 
```json
  {
      "success": "success", 
      "message": "All Uers retrived successfully",
      "data": [{},{}...], 
  }
```

### Send message to any of the registered user

Route:  api/v1/addmsg (POST)

Request body:

```json
 {
    "message":"",  //Message to send
    "sender":"",   //Sender Id
    "reciver":"",  //Reciver Id
    "createdAt":"" //Time Stamp
}

```
 
 Response:Sent message .

 Response Sample Pattern:

```json
 {
      "success": "success", 
      "message": "Message sent successfully",
      "data":  "" //Sent message
  }
```
### Get all conversations of a specific user           

Route:  api/v1/getallmessages (GET)

Request body:

```json
 {
    "sender":"",   //Sender Id
    "reciver":"",  //Reciver Id
}

```
 
 Response:Retrive all messages .

 Response Sample Pattern:

```json
 {
      "success": "success", 
      "message": "Message sent successfully",
      "data":  [{},{}....] //Sent message
  }
```

### Error Handling:
Error Response Object include the following properties:
- success  →  false
- message → Error Type → Validation Error, Cast Error, Duplicate Entry
- errorMessages 
- stack

### Sample Error Response

```json
   {
    "success": false,
    "message": "E11000 duplicate key error collection: univerity-management.students index: email_1 dup key: { email: \"user2@gmail.com\" }",
    "errorMessages": [
        {
            "path": "",
            "message": "E11000 duplicate key error collection: univerity-management.students index: email_1 dup key: { email: \"user2@gmail.com\" }"
        }
    ],
    "stack": "MongoServerError: E11000 duplicate key error collection: univerity-management.students index: email_1 dup key: { email: \"user2@gmail.com\" }\n    at H:\\next-level-development\\university-management-auth-service\\node_modules\\mongodb\\src\\operations\\insert.ts:85:25\n    at H:\\next-level-development\\university-management-auth-service\\node_modules\\mongodb\\src\\cmap\\connection_pool.ts:574:11\n    at H:\\next-level-development\\university-writeOrBuffer (node:internal/streams/writable:391:12)"
}
```
