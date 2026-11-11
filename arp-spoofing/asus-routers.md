---
description: Thanks to @thecoolestminion at Discord
icon: router
---

# ASUS Routers

## Install Asuswrt-Merlin on ASUS Routers

### Contents

| # | Section                       | Covers                                      |
| - | ----------------------------- | ------------------------------------------- |
| 1 | Requirements                  | Parts list, supported models                |
| 2 | Preparation                   | Backups and downloads                       |
| 3 | Installation                  | Verify and flash the firmware               |
| 4 | Post-installation             | Confirm, reset, updates                     |
| 5 | Change Onboard MAC (optional) | Set the LAN (br0) MAC with a JFFS script    |
| 6 | Isolate a Device (optional)   | Block one device from all other LAN devices |
| 7 | Troubleshooting               | Fixes, rescue mode, revert to stock         |

{% hint style="danger" %}
* Only flash the file for your **exact model and hardware version**.
* **Never cut the power** or close the browser during a flash.
* **Never restore a stock settings backup into Merlin.**
{% endhint %}

### Requirements

#### Parts

| Item                         | Notes                                                       | Amazon                                                                                                                                                        |
| ---------------------------- | ----------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Computer                     | Windows, macOS, or Linux                                    | —                                                                                                                                                             |
| Ethernet cable               | Required for rescue mode                                    | [Cat6 cable](https://www.amazon.com/s?k=Cable+Matters+Cat6+Snagless+Ethernet+Cable+10+ft)                                                                     |
| Paperclip / SIM tool         | For the Reset button                                        | [SIM tool](https://www.amazon.com/s?k=SIM+card+ejector+tool+pack)                                                                                             |
| USB-to-Ethernet adapter      | Only if there's no Ethernet port. Test it before flash day. | [USB-C](https://www.amazon.com/s?k=UGREEN+USB+C+to+Ethernet+Adapter+Gigabit) · [USB-A](https://www.amazon.com/s?k=UGREEN+USB+3.0+to+Ethernet+Adapter+Gigabit) |
| USB flash drive _(optional)_ | For Merlin add-ons (amtm)                                   | [Samsung FIT Plus](https://www.amazon.com/s?k=Samsung+FIT+Plus+64GB+USB+3.1+Flash+Drive)                                                                      |
| UPS _(optional)_             | Guards against power loss mid-flash                         | [APC BE600M1](https://www.amazon.com/s?k=APC+Back-UPS+BE600M1)                                                                                                |

#### Supported routers

Check the label under the router for the model and **H/W Ver** (`2.0` = V2). **V1 and V2 firmware are not interchangeable.**

| Source                                                         | Models                                                                                                                                                                                                             | File                     |
| -------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------ |
| [Merlin](https://www.asuswrt-merlin.net/download) 3004.388     | RT-AX58U V1 / RT-AX3000 V1, RT-AX68U, RT-AX86U / RT-AX86S, RT-AX88U, GT-AX11000, GT-AXE11000                                                                                                                       | `.w`                     |
| [Merlin](https://www.asuswrt-merlin.net/download) 3006.102     | RT-AX86U Pro, RT-AX88U Pro, GT-AX6000, GT-AX11000 Pro, GT-AXE16000, ZenWiFi Pro XT12, RT-BE58 Go, RT-BE86U, RT-BE88U / RT-BE7200, RT-BE92U, RT-BE96U, GT-BE98 Pro, GT-BE19000AI                                    | `.pkgtb`                 |
| [Gnuton](https://github.com/gnuton/asuswrt-merlin.ng/releases) | TUF-AX3000 V1 and V2, TUF-AX5400, RT-AX58U V2 / RT-AX3000 V2, RT-AX82U V1 and V2, RT-AX5400, RT-AX92U, DSL-AX82U / DSL-AX5400, ZenWiFi XT8 (RT-AX95Q V1), ZenWiFi ET8 (RT-AXE95Q), GT-BE98 / GT-BE25000, DSL-AC68U | `.w` / `.pkgtb` / `.trx` |

Not listed means not supported. Checked November 2026.

### Preparation

Do this while you still have internet.

* [ ] **Write down** your WAN type and any PPPoE login or VLAN (**WAN → Internet Connection**), your Wi-Fi names and passwords, and your router login.
* [ ] **Back up settings:** **Administration → Restore/Save/Upload Setting → Save setting**. This backup is for stock firmware only.
* [ ] **Note your firmware version:** **Administration → Firmware Upgrade**.
* [ ] **Download the stock firmware and the Firmware Restoration tool** for your model from [asus.com/support](https://www.asus.com/support/) → **Driver & Utility**.
* [ ] _Optional:_ **Record your LAN MAC** with `arp -a`.

### Installation

{% stepper %}
{% step %}
#### Download

{% tabs %}
{% tab title="Merlin" %}
Download your model from [asuswrt-merlin.net/download](https://www.asuswrt-merlin.net/download) and **unzip it**. ROG models may include a `_rog` file, which is an experimental theme. Use the other file.
{% endtab %}

{% tab title="Gnuton" %}
Open the **Latest** release on [GitHub](https://github.com/gnuton/asuswrt-merlin.ng/releases) (skip **Pre-release**). Download your model's firmware **and** its `.md5`.
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
#### Verify

```powershell
Get-FileHash .\YOUR-FILE -Algorithm SHA256   # Merlin: compare with the download page
Get-FileHash .\YOUR-FILE -Algorithm MD5      # Gnuton: compare with the .md5 file
```

On macOS use `shasum -a 256` / `md5`. On Linux use `sha256sum` / `md5sum`. **If the hashes don't match, download again.**
{% endstep %}

{% step %}
#### Connect

Plug into a **LAN** port, not WAN. **Turn off any VPN** on your computer. Log in at [http://192.168.50.1](http://192.168.50.1).
{% endstep %}

{% step %}
#### Unlock (newer stock firmware only)

Only needed if your stock version is `3.0.0.6.102_37000` or higher. Turn on **Administration → System → Enable SSH: LAN only → Apply**. Then run these, using your router username in place of `admin`:

```bash
ssh admin@192.168.50.1
nvram set DOWNGRADE_CHECK_PASS=1
exit
```
{% endstep %}

{% step %}
#### Reboot, then upload

1. Click **Reboot**, wait 2 minutes, and log in again.
2. Go to **Administration → Firmware Upgrade → Manual firmware update → Upload**.
3. Choose the `.w` / `.pkgtb` file, **not** the `.zip` or `.md5`.
{% endstep %}

{% step %}
#### Wait 5 minutes

Don't touch anything, even if the page looks stuck. Wi-Fi will drop.
{% endstep %}
{% endstepper %}

### Post-installation

* **Confirm:** the firmware version shows Merlin, for example `3004.388.13_0`, `3006.102.9_0`, or `3004.388.11_1-gnuton1`. Settings normally carry over.
* **Acting strange?** Go to **Administration → Restore/Save/Upload Setting → Factory default**. Then set the router up by hand, using the same Wi-Fi name and password.
* **Back up again** and label the file as a Merlin backup.
* **Updates:** use the same upload page. No reset is needed.

### Change Onboard MAC (optional)

This is only for cases where the LAN MAC changed after flashing and a device depends on the old one. It re-applies the MAC at boot, after any service restart, and every minute.

{% hint style="warning" %}
Use the router's **own original MAC**. Never use a MAC that another device on your network has.
{% endhint %}

{% stepper %}
{% step %}
#### Get the MAC (before flashing)

{% tabs %}
{% tab title="Windows" %}
```
ping -n 1 192.168.50.1
arp -a 192.168.50.1
```

Copy the **Physical Address**, for example `xx-xx-xx-xx-xx-xx`. Dashes are fine.
{% endtab %}

{% tab title="macOS / Linux" %}
```bash
ping -c 1 192.168.50.1
arp -n 192.168.50.1          # macOS
ip neigh show 192.168.50.1   # Linux
```

macOS drops leading zeros (`4:d9:…`). Add them back (`04:d9:…`).
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
#### Enable JFFS scripts and SSH

Go to **Administration → System**. Set **Enable JFFS custom scripts and configs** to **Yes** and **Enable SSH** to **LAN only**, then click **Apply**. Connect with:

```bash
ssh admin@192.168.50.1
```
{% endstep %}

{% step %}
#### Create the script

```bash
mkdir -p /jffs/scripts
cat > /jffs/scripts/br0-mac.sh <<'EOF'
#!/bin/sh
# Pins the LAN bridge (br0) MAC address.
# Put the MAC from "arp -a" on the next line. Dashes or colons, any case.
MAC="PUT-YOUR-MAC-HERE"

WANT="$(echo "$MAC" | sed 's/-/:/g; s/ //g' | tr 'abcdef' 'ABCDEF')"
if ! echo "$WANT" | grep -Eq '^([0-9A-F]{2}:){5}[0-9A-F]{2}$'; then
  echo "br0-mac: '$MAC' is not a valid MAC. Edit /jffs/scripts/br0-mac.sh" >&2
  exit 1
fi

[ -e /sys/class/net/br0/address ] || exit 0
cur() { tr 'abcdef' 'ABCDEF' < /sys/class/net/br0/address; }

OLD="$(cur)"
[ "$OLD" = "$WANT" ] && exit 0

ifconfig br0 hw ether "$WANT"
logger -t br0-mac "br0 was $OLD, set to $WANT, now $(cur)"
EOF
chmod 755 /jffs/scripts/br0-mac.sh
```
{% endstep %}

{% step %}
#### Add startup hooks

```bash
for f in services-start service-event-end; do
  [ -f /jffs/scripts/$f ] || echo '#!/bin/sh' > /jffs/scripts/$f
  chmod 755 /jffs/scripts/$f
done

grep -q br0-mac /jffs/scripts/services-start || cat >> /jffs/scripts/services-start <<'EOF'
/jffs/scripts/br0-mac.sh
cru a br0mac "* * * * * /jffs/scripts/br0-mac.sh"
EOF

grep -q br0-mac /jffs/scripts/service-event-end || \
  echo '(sleep 5; /jffs/scripts/br0-mac.sh) &' >> /jffs/scripts/service-event-end
```

This adds to existing scripts rather than replacing them, so amtm add-ons keep working. It's safe to paste twice.
{% endstep %}

{% step %}
#### Set your MAC

Open the script with `nano /jffs/scripts/br0-mac.sh` and replace `PUT-YOUR-MAC-HERE`. Save with **Ctrl+O**, **Enter**, then **Ctrl+X**. Or use one command:

```bash
sed -i 's/^MAC=.*/MAC="xx-xx-xx-xx-xx-xx"/' /jffs/scripts/br0-mac.sh
```
{% endstep %}

{% step %}
#### Test

```bash
/jffs/scripts/br0-mac.sh
cat /sys/class/net/br0/address
```

The second command should print your MAC. SSH may freeze for about 30 seconds while your computer relearns the router's MAC. Then **reboot** and check again. Changes are logged as `br0-mac` in **System Log**.
{% endstep %}
{% endstepper %}

<details>

<summary>Undo</summary>

```bash
cru d br0mac
sed -i '/br0-mac/d' /jffs/scripts/services-start /jffs/scripts/service-event-end
rm /jffs/scripts/br0-mac.sh
reboot
```

</details>

### Isolate a Device (optional)

This blocks one device from every other device on the LAN, in both directions. It still has internet. It's confirmed working with the isolated device wired and the others on Wi-Fi. If both sides are wired, run the test in the last step.

Needs **JFFS custom scripts** and **SSH** turned on (**Administration → System**).

{% stepper %}
{% step %}
#### Find its MAC

Get the device's IP from **Network Map → Clients**, then run this over SSH:

```bash
ping -c 1 192.168.50.X >/dev/null; awk '$1=="192.168.50.X"{print $4}' /proc/net/arp
```

Then reserve that IP for the device: **LAN → DHCP Server → Manually Assigned IP**.
{% endstep %}

{% step %}
#### Create the script

```bash
mkdir -p /jffs/scripts
cat > /jffs/scripts/isolate.sh <<'EOF'
#!/bin/sh
# Isolates one device from the rest of the LAN. Internet still works.
MAC="PUT-THE-DEVICE-MAC-HERE"

WANT="$(echo "$MAC" | sed 's/-/:/g; s/ //g' | tr 'ABCDEF' 'abcdef')"
echo "$WANT" | grep -Eq '^([0-9a-f]{2}:){5}[0-9a-f]{2}$' || { echo "isolate: bad MAC '$MAC'" >&2; exit 1; }

ebtables -N ISOLATE 2>/dev/null
ebtables -P ISOLATE RETURN
ebtables -F ISOLATE
ebtables -A ISOLATE -s "$WANT" -j DROP
ebtables -A ISOLATE -d "$WANT" -j DROP
ebtables -L FORWARD | grep -q -- '-j ISOLATE' || ebtables -I FORWARD -j ISOLATE
EOF
chmod 755 /jffs/scripts/isolate.sh
```
{% endstep %}

{% step %}
#### Set the MAC and add startup hooks

Replace `xx:xx:xx:xx:xx:xx` with the MAC from the first step:

```bash
sed -i 's/^MAC=.*/MAC="xx:xx:xx:xx:xx:xx"/' /jffs/scripts/isolate.sh

for f in services-start service-event-end; do
  [ -f /jffs/scripts/$f ] || echo '#!/bin/sh' > /jffs/scripts/$f
  chmod 755 /jffs/scripts/$f
done

grep -q isolate.sh /jffs/scripts/services-start || cat >> /jffs/scripts/services-start <<'EOF'
/jffs/scripts/isolate.sh
cru a isolate "* * * * * /jffs/scripts/isolate.sh"
EOF

grep -q isolate.sh /jffs/scripts/service-event-end || \
  echo '(sleep 5; /jffs/scripts/isolate.sh) &' >> /jffs/scripts/service-event-end
```
{% endstep %}

{% step %}
#### Turn on and verify

```bash
/jffs/scripts/isolate.sh
cru a isolate "* * * * * /jffs/scripts/isolate.sh"
ebtables -L ISOLATE
```

You should see two `-j DROP` lines with the device's MAC. Then, on the isolated device, open PowerShell **as admin**:

```powershell
arp -d *
ping 192.168.50.Y        # another LAN device
arp -a
```

If it's isolated, the ping shows `Destination host unreachable` and the other device's IP is **missing** from `arp -a`. The router (`192.168.50.1`) still appears, which is expected.
{% endstep %}
{% endstepper %}

<details>

<summary>Undo</summary>

```bash
ebtables -D FORWARD -j ISOLATE; ebtables -F ISOLATE; ebtables -X ISOLATE
cru d isolate
sed -i '\#/jffs/scripts/isolate.sh#d' /jffs/scripts/services-start /jffs/scripts/service-event-end
rm /jffs/scripts/isolate.sh
```

</details>

### Troubleshooting

**Wait 10 minutes first.** A router that's still flashing can look dead.

| Problem           | Fix                                                                                                                                             |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| Page won't open   | Turn off VPN, use a LAN port, and try [router.asus.com](http://router.asus.com). The router's address is the **Default Gateway** in `ipconfig`. |
| Firmware rejected | Check the model and version. Upload the `.w` / `.pkgtb`, not the `.zip` / `.md5`. Reboot and retry. On newer stock, do the unlock step.         |
| No internet       | Restart the modem, then the router. Re-check your WAN settings under **WAN → Internet Connection**.                                             |
| Forgot password   | With the router on, hold **Reset** for 5–10 seconds until the power light blinks. Then set it up again.                                         |

#### Rescue mode

Use this when the router won't boot.

1. Unplug the power. Hold **Reset** while you plug it back in, and release when the power light **blinks slowly** (about 5–10 seconds).
2. Connect by cable. Set your computer's IP to `192.168.1.10` with mask `255.255.255.0`. On Windows: **Win+R → `ncpa.cpl` → Ethernet → Properties → IPv4**.
3. Upload the **stock** firmware with ASUS **Firmware Restoration**, or at [http://192.168.1.1](http://192.168.1.1).
4. Wait 5 minutes, then **set your computer's IP back to automatic**.

#### Revert to stock

Upload the stock firmware on **Firmware Upgrade**, then factory reset. Restore your stock backup or set up by hand.

***

[SNBForums](https://www.snbforums.com/forums/asuswrt-merlin.42/) · [Merlin wiki](https://github.com/RMerl/asuswrt-merlin.ng/wiki) · Unofficial guide, not affiliated with ASUS, RMerlin, or Gnuton.
