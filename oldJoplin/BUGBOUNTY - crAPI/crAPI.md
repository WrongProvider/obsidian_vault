crAPI

```
 `LOGIN: "api/auth/login",
        UNLOCK: "api/auth/unlock",
        GET_USER: "api/v2/user/dashboard",
        SIGNUP: "api/auth/signup",
        RESET_PASSWORD: "api/v2/user/reset-password",
        FORGOT_PASSWORD: "api/auth/forget-password",
        VERIFY_OTP: "api/auth/v3/check-otp",
        LOGIN_TOKEN: "api/auth/v4.0/user/login-with-token",
        ADD_VEHICLE: "api/v2/vehicle/add_vehicle",
        GET_VEHICLES: "api/v2/vehicle/vehicles",
        RESEND_MAIL: "api/v2/vehicle/resend_email",
        CHANGE_EMAIL: "api/v2/user/change-email",
        VERIFY_TOKEN: "api/v2/user/verify-email-token",
        UPLOAD_PROFILE_PIC: "api/v2/user/pictures",
        UPLOAD_VIDEO: "api/v2/user/videos",
        CHANGE_VIDEO_NAME: "api/v2/user/videos/<videoId>",
        REFRESH_LOCATION: "api/v2/vehicle/<carId>/location",
        CONVERT_VIDEO: "api/v2/user/videos/convert_video",
        CONTACT_MECHANIC: "api/merchant/contact_mechanic",
        RECEIVE_REPORT: "api/mechanic/receive_report",
        GET_MECHANICS: "api/mechanic",
        GET_PRODUCTS: "api/shop/products",
        GET_SERVICES: "api/mechanic/service_requests",
        BUY_PRODUCT: "api/shop/orders",
        GET_ORDERS: "api/shop/orders/all",
        GET_ORDER_BY_ID: "api/shop/orders/<orderId>",
        RETURN_ORDER: "api/shop/orders/return_order",
        APPLY_COUPON: "api/shop/apply_coupon",
        ADD_NEW_POST: "api/v2/community/posts",
        GET_POSTS: "api/v2/community/posts/recent",
        GET_POST_BY_ID: "api/v2/community/posts/<postId>",
        ADD_COMMENT: "api/v2/community/posts/<postId>/comment",
        VALIDATE_COUPON: "api/v2/coupon/validate-coupon"
    };`

```

HTTP/1.1 200 OK

Server: openresty/1.25.3.1

Date: Fri, 28 Jun 2024 11:54:38 GMT

Content-Type: application/json

Connection: keep-alive

Access-Control-Allow-Headers: Accept, Content-Type, Content-Length, Accept-Encoding, X-CSRF-Token, Authorization

Access-Control-Allow-Methods: POST, GET, OPTIONS, PUT, DELETE

Access-Control-Allow-Origin: *

Content-Length: 1275

{"posts":\[{"id":"9wk2Z7v3mid8NCz2F7PwcK","title":"teste","content":"asdasd","author":{"nickname":"smokin","email":"smokin@hacker.com","vehicleid":"","profile\_pic\_url":"","created\_at":"2024-06-26T10:21:18.248Z"},"comments":\[\],"authorid":8,"CreatedAt":"2024-06-26T10:21:18.248Z"},{"id":"owaTQL9Fu4vrXrNYBuFuML","title":"Title 3","content":"Hello world 3","author":{"nickname":"Robot","email":"robot001@example.com","vehicleid":"4bae9968-ec7f-4de3-a3a0-ba1b2ab5e5e5","profile\_pic\_url":"","created\_at":"2024-06-26T08:36:26.593Z"},"comments":\[\],"authorid":3,"CreatedAt":"2024-06-26T08:36:26.593Z"},{"id":"3DarVuozLFKxzHoCJaZ7tD","title":"Title 2","content":"Hello world 2","author":{"nickname":"Pogba","email":"pogba006@example.com","vehicleid":"cd515c12-0fc1-48ae-8b61-9230b70a845b","profile\_pic\_url":"","created\_at":"2024-06-26T08:36:26.591Z"},"comments":\[\],"authorid":2,"CreatedAt":"2024-06-26T08:36:26.591Z"},{"id":"arxVCLYZh7xPiDs49dzBKP","title":"Title 1","content":"Hello world 1","author":{"nickname":"Adam","email":"adam007@example.com","vehicleid":"f89b5f21-7829-45cb-a650-299a61090378","profile\_pic\_url":"","created\_at":"2024-06-26T08:36:26.584Z"},"comments":\[\],"authorid":1,"CreatedAt":"2024-06-26T08:36:26.584Z"}\],"next\_offset":null,"previous\_offset":null,"total":4}