# wait-for-internet

So that I don't mash Refresh on a web page while I'm waiting for my laptop to have a remote connection.

```
wait-for-internet 0.1.2
Command line utility that waits till you have an internet connection.

USAGE:
    wait-for-internet [OPTIONS]

FLAGS:
    -h, --help       Prints help information
    -V, --version    Prints version information

OPTIONS:
        --text <text>          Text to display before dots while waiting [default: ]
    -t, --timeout <timeout>    Exits if a successful connection is not made within <timeout> seconds
    -w, --wait-time <wait>     Time to wait between failed requests [default: 0]
```

Exits successfully once it makes a successful request, see the [online](https://github.com/jesusprubio/online) crate for which URLs/fullbacks it uses to check for a remote connection.

### Install

Install [cargo](https://doc.rust-lang.org/cargo/getting-started/installation.html).

```
git clone https://github.com/seanbreckenridge/wait-for-internet
cd wait-for-internet
cargo build --bins --release  # you can add the '-j <CPU_COUNT>' flag to specify CPU count
# copy to somewhere on your $PATH
cp ./target/release/wait-for-internet /usr/local/bin/
wait-for-internet  # test the script
```

#### Example Usage

On Mac, one can do something like:

`wait-for-internet && afplay /System/Library/Sounds/Funk.aiff`

... or:

`wait-for-internet --text "(waiting for internet)" && say "You have internet"`

I have an alias setup on my machine that plays the default 'message' sound and sends a notification:

`alias wfi='wait-for-internet && notify-send "INTERNET" && mpv /usr/share/sounds/freedesktop/stereo/message.oga > /dev/null 2>&1'`

Can also be used in situations to verify you have internet before calling some other command:

`wait-for-internet && xdotool search --class "Firefox" key --window %@ "ctrl+r"` (refresh firefox after you have internet)

`wait-for-internet && sudo apt update && sudo apt upgrade`

`wait-for-internet && speedtest-cli`

`wait-for-internet && ssh <somewhere>`

`wait-for-internet && fg` (resume some suspended task that requires internet)

