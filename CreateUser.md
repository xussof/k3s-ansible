sudo su
adduser pi
usermod -aG sudo pi

grep -qxF 'pi ALL=(ALL) NOPASSWD: ALL' /etc/sudoers || echo 'pi ALL=(ALL) NOPASSWD: ALL' | sudo tee -a /etc/sudoers


pass: seqp7nC4310b