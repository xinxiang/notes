* [How-to-interpret-SPF-authentication-verification-results](https://help.returnpath.com/hc/en-us/articles/115000460632-How-to-interpret-SPF-authentication-verification-results)
* [BrokenPipeError](http://postfix.1071664.n5.nabble.com/Some-people-sending-to-us-getting-451-4-3-5-Server-configuration-rejections-td70280.html)

> First. the script should limit the time for DNS lookups.
> Second, the script should not die after BrokenPipeError exceptions.
> try: sys.stdout.flush()
> except BrokenPipeError: pass

On my mail server:
```
Jul 28 14:52:36 www policyd-spf[88248]: Pass; identity=helo; client-ip=104.47.60.53; helo=can01-qb1-obe.outbound.protection.outlook.com; envelope-from=...@utoronto.ca; receiver=...@doe.utoronto.ca
Jul 28 14:53:02 www policyd-spf[88246]: Temperror; identity=mailfrom; client-ip=104.47.60.53; helo=can01-qb1-obe.outbound.protection.outlook.com; envelope-from=...@utoronto.ca; receiver=...@doe.utoronto.ca
Jul 28 14:53:02 www policyd-spf[88246]: Traceback (most recent call last):
Jul 28 14:53:02 www policyd-spf[88246]:   File "/usr/bin/policyd-spf", line 741, in <module>
Jul 28 14:53:02 www policyd-spf[88246]:     sys.stdout.flush()
Jul 28 14:53:02 www policyd-spf[88246]: BrokenPipeError: [Errno 32] Broken pipe
```
```
# grep -A3 -B3 'flush' /usr/bin/policyd-spf
            sys.stdout.write('action=dunno\n\n')

        #  end of record  {{{3
        sys.stdout.flush()
        data = {}
        continue
```

A sender received a failed delivery message; but a couple days later, that email seemed delivered.
