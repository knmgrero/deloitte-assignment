# Deloitte Assignment - Order API


## API Description
This API contains single resource "Order" and allows the following

#### /order
  ##### `GET`| List orders
  ##### `POST`| Create a new order 

#### /order/{id}
  ##### `GET`| Get order details by Id
  ##### `PUT`| Update an order by Id
  ##### `DELETE`| Delete an order by Id

#### User Case 1
Client initially calls /order/GET to get full copy of order list. Server also sends "Last-Modified" in response header.
After 5 minutes client calls /order/GET with "If-Modified-Since"=*Last-Modified* in request header. Then server will send the full order list again if and only if the collection was modified since Last-Modified.

#### User Case 2
When mobile application calls /order/GET, it will send optional paging parameters to avoid full loading of order list in one call. Also a light-weight OrderSummary object is used rather than full Order object when listing orders.

#### User Case 3
This API has been designed with parameterized resource types. Due to generic implementation no additional code is required to extend similar CRUD operation for other future resources customer & product

#### Other Design Considerations

1) Use of version number in resource record to avoid possible data overwritting.
2) Use of standard & logical HTTP error codes for exception handling.
3) Define maximum sizes for string variable to handle edge scenarios.


#### @Auther Nishantha Manosh Grero

