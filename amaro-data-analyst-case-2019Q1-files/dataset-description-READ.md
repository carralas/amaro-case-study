## The relationship of the tables is the following
order_items.order_id = orders.id --(Nx1)
order_items.sku = products.sku --(Nx1)
orders.user_id = customers.user_id --(Nx1)

## Fields description
1. Payment Methods
orders.payment_method -- describe the payment method of the order, if the method is boleto or others, like credit card

2. Order Status & KPIs
In AMARO there are two main moments for the order:
 - when a order is placed, which means the customer finalizes the purchase process, but hasn't receive the product yet (the column 'orders.is_placed_order'=true indicates that)
 - when a order is shipped, which means the customer received the product (the column 'orders.is_shipped_orders'=true indicates that)
 If an order is placed and not shipped, it means the customer finalized the checkout process, however didn't pay the boleto or cancelled the purchase.
 Those two flags mentioned above summarize the combinations of 'order_status' and 'order_channel_code_online'.

 AMARO has two KPIs related to revenue:
  - GMV -- which is the sum of the column order_total when is_placed_order = true
  - Gross Revenue -- which is the sum of the column order_total when is_shipped_order = true

The case study is interested on orders that were placed (is_placed_order = true) and not shipped (is_shipped_order = false) through payment_method=boleto. And the goal is to maximize the Gross Revenue.

3. All other columns:
You can use any of the other columns to have the necessary insights, even the 'id' columns.
