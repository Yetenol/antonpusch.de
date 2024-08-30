
| Resource     | Distance | Transport medium                            |
| ------------ | -------- | ------------------------------------------- |
| items        | short    | belts                                       |
| fluids       | short    | pipes                                       |
| items/fluids | medium   | item/fluid busses with 4 lanes per item     |
| items/fluids | long     | trains with requester and provider stations |

- order 2 rows max
- use Spidertrons for bulk orders
- Belts transport resources over short distances
- Resource busses transport resources over short distances
- Trains transport resources over long distances using requester and provider stations
- Pipes transport fluids over short distances
- Fluid busses transport fluids over long distances
- Logistic bots only supply players
- Tag building plans on the map
- Separate each component into its own block
- Faster long inserters aren't in the game for a reason [Long Inserters](./content/long%20inserters.md)

# Robots

- Filter some inventory slots at the bottom and request a stack each
- Don't request intermediates