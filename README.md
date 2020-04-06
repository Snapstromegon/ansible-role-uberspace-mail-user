# Ansible Role: uberspace-mail-user

This is part of the uberspace roles collection.

This is meant to be used on your [Uberspace](https://uberspace.de/).

Please be aware, that I'm neither part of the Uberspace team, nor am I associated to them other than having some Uberspaces myself.
This project was created, because I wanted to use the roles for myself and thought they were okay-ish enough to share them.

## What is this (from the uberspace manual)

You can use mailboxes in the form of $MAILBOX@$USER.uber.space. If you have set up additional domains, $MAILBOX@$DOMAIN will also work.

You can find the documentation of the replaced tool `uberspace mail user` in the Uberspace Manual [here](https://manual.uberspace.de/mail-mailboxes.html).

## Notes

Because I didn't yet find out how to solve idempotency, this role currently doesn't support changing a users password!

I'll try to add this in the future. If you have an idea, feel free to contribute in .

## Usage

| Variable | Choices/Default                            | Description                                                                |
| :------: | :----------------------------------------- | :------------------------------------------------------------------------- |
|   user   |                                            | The mailbox user to use as user                                            |
| password |                                            | The password for the user (use e.g. ansible-vault)                         |
|  state   | <ul><li>present ✔</li><li>absent</li></ul> | "present" to enable the user, "absent" to disable it                       |
|  users   | []                                         | A list of user, password, state combinations to set multiple users at once |

## Examples

### Add user

```yaml
- hosts: uberspace
  roles:
    - name: uberspace-mail-user
      user: post
      password: yourtotalysecretpassword
```

### Delete user

```yaml
- hosts: uberspace
  roles:
    - name: uberspace-mail-user
      user: post
      state: absent
```

### Set multiple users

```yaml
- hosts: uberspace
  roles:
    users:
      - name: uberspace-mail-user
        user: post
        password: yourtotalysecretpassword
      - name: uberspace-mail-user
        user: deleteme
        state: absent
```
