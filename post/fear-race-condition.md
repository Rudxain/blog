# My (ir)rational fear of [race conditions](https://en.wikipedia.org/wiki/Race_condition)
As an example of what I mean (and to justify/[rationalize](https://en.wikipedia.org/wiki/Rationalization_(psychology)) my mild phobia), consider this real-life scenario:
1. You want to delete a WhatsApp chat (either by deleting the whole chat, or only the contents via "Clear chat")
2. You're about to confirm the prompt
3. Mere _miliseconds_ before you hit the confirmation button, the other person sends you a message
4. Congrats! you've **deleted an unread message**

I don't remember this ever happening to me, but I am sure it has happened to someone else. I'm worried that I might "ignore" someone's message, or that they "ignore" mine. I don't want to be rude!

My workaround? turn off all internet connections before deletion. That way, WA cannot recieve the message until I've decided to reconnect.

But this begs the question: what happens if I **disconnect while I'm recieving** a message? Does WA take care of that? Does the Android system take care of that? Can TCP save us?

I don't trust most developers implementing those systems to handle that properly, because I can't even trust _myself_ to do it properly.

Have you heard of [TOCTTOU](https://en.wikipedia.org/wiki/Time-of-check_to_time-of-use)? every programmer/coder has made that mistake, even pros can forget about handling that.

A related example with tested consequences is this: [I use a local VPN](https://github.com/M66B/NetGuard), and I've noticed that Android doesn't connect to VPN until the user "logs in" (input PIN) for the 1st time after reboot, but it does connect to the internet before login! So I developed the habit of disconnecting from the internet before rebooting, to ensure VPN is connected before any network packets are sent. A bit too paranoid? perhaps :v

## See also
- [David Wheeler on this topic](https://dwheeler.com/secure-programs/Secure-Programs-HOWTO/avoid-race.html)
