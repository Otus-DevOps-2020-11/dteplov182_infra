# dteplov182_infra
dteplov182 Infra repository

## ДЗ 3
Команда для прыжка через бастион во внутренную машину с передачей ключа:
```bash
ssh -t -i <KEYFILE> -A <BASTION_USER>@<BASTION_IP> 'ssh <INTERNAL_IP>'
```
**-t**      Force pseudo-tty allocation.

**-i** identity_file

**-A**      Enables forwarding of the authentication agent connection.

**Либо можно использовать ключ** **-J**

Настроим SSH для подключеня сразу к внутренней машине используя алиасы ssh:

```bash
cat ~/.ssh/config
Host bastion
        Hostname <BASTION_IP>
        User <BASTION_IP>
        IdentityFile <KEYFILE>
        ForwardAgent yes
Host someinternalhost
        Hostname <INTERNAL_IP>
        User <INTERNAL_USER>
        ProxyJump bastion
```


bastion_IP = 84.201.172.12
someinternalhost_IP = 10.130.0.28

