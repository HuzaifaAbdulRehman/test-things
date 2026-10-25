# Smart Home Mashup

You want to automate a small part of your home. The room setup can be seen in the illustration below.
![Quickstart Setup](./assets/quickstart-setup.svg)

Each morning, when you wake up and go towards the kitchen area, you want the coffee to be brewed automatically.
Your task is to write a script that brews the coffee of your choice when you pass in front the presence sensor in the kitchen if it is earlier than 13:00 but later than 5:00.

This mashup consist of three Things:

-   Presence Sensor (MQTT)
-   Simple Coffee Machine (HTTP)
-   Smart Clock (CoAP)

Their logic is written in TypeScript and ran with the help of node-wot.
Their .ts files can be found under [things](./things/) folder.
Mashup's main code is located at [index.ts](./index.ts).

## Running the Mashup

After `npm run build` is executed, .ts files be compiled and executable JavaScript files will be available under [dist](./dist/).
One can run all Things manually or using the [runMashupThings](./runMashupThings.sh) script.
After Things start running, the main mashup logic can be run using the command `node ./dist/index.js`.

## Running with Docker

Every Thing and the main logic have separate docker files.

## Smart Clock Addresses

`SMART_CLOCK_HOSTNAME` sets the clock's listening address and defaults to `localhost`.
Set `SMART_CLOCK_PUBLIC_HOSTNAME` to the hostname clients should use in the generated Thing Description forms.
When it is unset or empty, node-wot keeps its automatic address discovery.
The production Compose file sets it from `STACK_HOSTNAME`.
The local stack keeps automatic discovery so the mashup can use the clock's container address instead of its own `localhost`.
