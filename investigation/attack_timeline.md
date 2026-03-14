
# Attack Timeline

The following timeline was reconstructed from the authentication logs.

| Time | Activity |
|------|----------|
| 09:00 | External IP 185.23.45.2 generated multiple failed login attempts against user john |
| 09:01 | The same IP successfully logged in to john's account |
| 09:04 | More failed login attempts were observed from the same IP |
| 09:05 | Another successful login followed the failures |
| 09:07 | Repeated brute force pattern continued |
| 09:08 | Another successful login occurred |
| 09:10 | Additional failed attempts observed |
| 09:11 | Successful authentication observed again |
| 09:13 | Final burst of failed login attempts detected |
| 09:14 | Final successful login from the same external IP |

## Summary
The repeated pattern of failed login attempts followed by successful authentication from the same external IP strongly indicates a brute force login attack against user john.
