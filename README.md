# Vmware_resolver
Vmware_resolver
Vmware_resolver

# sudo apt install -y build-essential dkms git iw

# git clone https://github.com/mkubecek/vmware-host-modules
# git checkout workstation-17.5.1
# git checkout workstation-17.5.1
# sudo make
# sudo install

$ sudo vmware-modconfig --console --install-all

$ openssl req -new -x509 -newkey rsa:2048 -keyout VMWARE15.priv -outform DER -out VMWARE15.der -nodes -days 36500 -subj "/CN=VMWARE/"

$ sudo /usr/src/linux-headers-$(uname -r)/scripts/sign-file sha256 ./VMWARE15.priv ./VMWARE15.der $(modinfo -n vmmon)

$ sudo /usr/src/linux-headers-$(uname -r)/scripts/sign-file sha256 ./VMWARE15.priv ./VMWARE15.der $(modinfo -n vmnet)

$ tail $(modinfo -n vmmon) | grep "Module signature appended"

$ sudo mokutil --import VMWARE15.der

now reboot

$ reboot

run below command after Reboot

$ mokutil --test-key VMWARE15.der
