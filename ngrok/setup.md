### Solution

- Download and install ngrok https://ngrok.com/

- Sign Up

- Get Auth Token

- Run Command (in Terminal): 

`ngrok config add-authtoken <YOUR_AUTH_TOKEN>`

Copy the command provided on your dashboard (https://ngrok.com/). 
Replace <YOUR_AUTH_TOKEN> with your actual token.

- Start a tunnel

**How to Start a Tunnel**

Start  Frontend racetrack/frontend: 

`npm run dev`

Start Backend racetrack/server

`npm run dev`

Start a Frontend tunnel.  In a new terminal, run ngrok:

`ngrok http 5173`

Open the frontend ngrok and copy URL (e.g., https://xyz-789.ngrok.io) and open in your phone's browser.