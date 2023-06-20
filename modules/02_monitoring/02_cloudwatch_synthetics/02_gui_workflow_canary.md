# GUI Workflow Canaries

Synthetics can also automate actions in the UI.

1. From the `Synthetics Canaries` console click `Create canary`.
2. Select `GUI workflow builder`.
3. Enter `yelb-click` for the name.
4. Enter the DNS name of the load balancer for URL.
5. Under workflow builder add a `Click` action.
6. Get the selector for one of the buttons from the Yelb UI. (ex. /html/body/yelb/html/body/div/div/div/div/div[2]/div[1]/div/div[2]/button)
7. Repeat for the rest of the buttons.