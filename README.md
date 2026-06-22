This program is intended to run only on payer's (community administrator's) PC as it has no security at all. It does not work on Windows XP!

On Linux, start the program with the ./orr command or the ./crc command for older version with the terminal opened from your right-click menu from the program's folder. Newer Windows builds start from orr.exe in the program directory. Or crc.exe for older builds.

After starting, the program will open in your browser. If you see a terminal has opened, keep it open during the duration of the use of the program. Close it to terminate the program.

Linux users should install sqlite3.

To compile you need Rust with cargo. I recommend https://rustup.rs

Install **libsqlite3-dev**

Windows build requires **sqlite3.dll** in the target/{debug, release}/deps folder.

Cross compiling for Win on Linux
--------------------------------
Put **sqlite3.dll** into target/i686-pc-windows-gnu/{debug,release}/deps.
Also on Debian (and possibly others) do:

    sudo apt-get install mingw-w64-i686-dev gcc-mingw-w64-i686
    sudo ln -s /usr/i686-w64-mingw32/lib/libadvapi32.a /usr/i686-w64-mingw32/lib/libAdvapi32.a

and create an empty document and give it the name config.toml in .cargo in your /home directory with rustflags only for i686:

    [target.i686-pc-windows-gnu]
    linker = "i686-w64-mingw32-gcc"
    rustflags = "-C panic=abort"

to build the Windows version, run:

    cargo build --target i686-pc-windows-gnu -v

