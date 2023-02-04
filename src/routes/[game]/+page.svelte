<script>
import * as Ably from "ably";
import jsoning from "jsoning";
import { page } from '$app/stores';
import { onMount } from "svelte";
import { Pname } from '../../stores.js';

let name, data;

Pname.subscribe((value) => {
		name = value;
	});

onMount(() => {
    let db = new jsoning("db.json");
    const ably = new Ably.Realtime.Promise({
      key: import.meta.env.ABLY_API_KEY,
      clientId: name,
    });
});
async function doPubSub() {
  // Ably code
  await realtime.connection.once("connected");
  console.log("Connected to Ably!");

  const channel = realtime.channels.get(page.path);

  await channel.subscribe((msg) => {
    console.log("Received: " + JSON.stringify(msg.data));
  });
  await channel.publish("update", { team: "Man United" });
}

doPubSub();

</script>

<div>
    <p>
    </p>
</div>

<style>

</style>