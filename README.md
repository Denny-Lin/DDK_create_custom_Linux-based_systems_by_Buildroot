# DDK_create_custom_Linux-based_systems(Buildroot)
Use the Buildroot to create custom Linux-based systems.

Host machine <br/>
uname -a <br/>
inux ubuntu-linux-20-04-desktop 5.13.0-25-generic #26~20.04.1-Ubuntu SMP Sat Jan 8 18:05:46 UTC 2022 aarch64 aarch64 aarch64 GNU/Linux &nbsp;

Target machine <br/>
arm &nbsp;

# Download the source files of the buildroot
ls  <br/>
cd Desktop/  <br/>
sudo apt install git <br/>
git clone git://git.buildroot.net/buildroot <br/>
cd buildroot/ &nbsp;

# Build images
make qemu_arm_versatile_defconfig <br/>
make &nbsp;

![Screen Shot 2022-02-27 at 1 15 14 PM](https://user-images.githubusercontent.com/67073582/155870630-fe357d0b-567c-47dd-b79d-051c7ee1ade6.png) &nbsp;

# Run on QEMU
sudo apt install qemu-system-arm <br/>

qemu-system-arm -M versatilepb -kernel output/images/zImage -dtb output/images/versatile-pb.dtb -drive file=output/images/rootfs.ext2,if=scsi,format=raw -append "root=/dev/sda console=ttyAMA0,115200" -serial stdio -net nic,model=rtl8139 -net user &nbsp;

buildroot login: root &nbsp;

![Screen Shot 2022-02-27 at 2 16 32 PM](https://user-images.githubusercontent.com/67073582/155870744-7eee022d-b4f3-4575-b7f7-021e1dbc1523.png) &nbsp;


