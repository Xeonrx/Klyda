<p align="center">
 <img src="https://github.com/Xeonrx/Resprayd/blob/main/img/fronticon.png">
</p>

The Klyda project has been created to aid in quick credential based attacks against online web applications.<br />
Klyda supports the use from simple password sprays, to large multithreaded dictionary attacks.

Klyda is a new project, and I am looking for any contributions; including wordlists contributions. Any help is very appreciated.
The script works by injecting given credentials into requests, and narrowing down successful results via blacklists of strings, status codes, or content lenghts.

Klyda offers simple, easy to remember usage; however, still offers configurability for your needs:
- Mulithreaded tasks
- Combine wordlists for larger scale attacks
- Blacklisting data to narrow down results
- Limit thread speed for sneaky purposes
- Alter requests, such as useragent, timeout, & headers
- File output

<p align="center">
 <img src="https://github.com/Xeonrx/Klydaa/blob/main/img/example.gif">
</p>

# Installation & Usage
**1)** Clone the Git repo to your machine, `git clone https://github.com/Xeonrx/Klydaa/edit/main/README.md`<br />
**2)** Cd into the Klyda directory, `cd Klyda`<br />
**3)** Install the neccessary modules via Pip, `pip install requests, beautifulsoup4`<br />
**4)** Display the Klyda help prompt for usage, `python3 klyda.py -h`

>Klyda has been tested on Windows & Linux, but should work on any machine capable of running Python.


What Klyda needs to work are only four simple dependencies: URL to attack, username(s), password(s), and a payload to send the data.
## The URL
You can parse the URL via the ``--url`` tag. It should look something like this, `--url http://127.0.0.1`<br />
Remember to **never** launch an attack on a webpage, that you don't have proper permission to do so.
## Usernames
Usernames are the main target to these dictionary attacks. It could be a whole range of usernames, a few in specific, or perhaps just one.
That's all your decision when using the script. You can specify usernames in a few ways...

**1)** Specify them manually, `-u Admin User123 Guest`<br />
**2)** Give a file to use, or a few to combine, `-U users.txt extra.txt`<br />
**3)** Give both a file & manual entry, `-U users.txt -u Johnson924`
## Passwords
Passwords are the hard part to these attacks. You don't know them, hence why dictionary & brute force attacks exists. Like the usernames, you can
give from just one password, up to however many you want. You can specify passwords in a few ways...

**1)** Specify them manually, `-p password 1234 letmein`<br />
**2)** Give a file to use, or a few to combine, `-P passwords.txt extra.txt`<br />
**3)** Give both a file & manual entry, `-P passwords.txt -p redklyda24`
## Payloads
Payloads are how you form the request, so the target website can take it in, and process it. Usually you would need to specify a: username value, a password value, and sometimes an extra value. You can see the form data your target uses by reviewing the network tab, of your browsers inspect element. For Klyda, you use the `-d` tag.<br />

You need to use placeholders to Klyda knows where to fill in the username & password, when fowarding out its requests. It may look something like this...
`-d username:xuser password:xpass Login:Login`

`xuser` is the placeholder to inject the usernames, & `xpass` is the placeholder to inject the passwords. Make sure you know these. If it is really neccessary, 
you can change the placeholder values with `-ph (value1) (value2)`

Parameters are formatted with `(key):(value)`

## Rate limiting
Credential attacks can be **very** loud on a network; hence, are detected easily. A targeted account could simply just receieve a simple lock due to too many
login attempts. This creates a DoS attack, but prevents you from gaining the users's credentials, which is the goal of Klyda.

So to make these attacks a little less loud, you can take use of the `--rate` tag. This allows you to limit threads to a certain number of requests per minute.<br />
It will be formatted like this, `--rate (# of requests) (minutes)`

For example, `--rate 5 1` will only send out 5 requests for each minute. Remember however, this is for each thread. If you had 2 threads, this would send 10 requests per minute.

## Example
Test Klyda out on the Damn Vulnerable Web App (DVWA)

`python3 klyda.py --url http://127.0.0.1/dvwa/login.php -u user guest admin -p 1234 password admin -d username:xuser password:xpass Login:Login --bstr "Login failed"`
## The Future
Like mentioned earlier, Klyda is still a work in progress. For the future, I plan on adding more functionality and reformating code for a cleaner look.

My top piority is to add proxy functionality, and am currently working on it.
