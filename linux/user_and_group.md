Add ${USER} to docker group

```
sudo usermod -aG docker ${USER}
```

```
su - ${USER}
```

List of the groups that the current user belongs to:
```
id -nG
```
