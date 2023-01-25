
# 204 : No Content success
*successful operation, and the user doesn't need to navigate away from it's current page*
- refresh token is succesfully deleted from db upon logging out.

# 400 : Bad Request
*request is recieved incorrectly because of bad formatting*

# 401 : Unauthorized
*request doesn't include the required authentication token*

# 403 : Forbidden
*client is forbidden from accessing a valid URL (token expired / unauthorized user)*

# 404 : Not Found
*requested route doesn't exist*

# 422 : Unprocessable Entity
*request is recieved correctly but it's missing some parameters*

# 502 : Bad Gateway
*database failure*

