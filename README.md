
<h2>
 Selamat datang  
<img src="https://media.giphy.com/media/hvRJCLFzcasrR4ia7z/giphy.gif" width="30px"/>
</h1>
<div align="center">
  <img src="https://media.giphy.com/media/dWesBcTLavkZuG35MI/giphy.gif" width="600" height="300"/>
</div>
<img align="center" src="https://github-readme-streak-stats.herokuapp.com?user=timcreative&theme=vue-dark&hide_border=true&date_format=M%20j%5B%2C%20Y%5D" alt="My github stats" />

<img align="center" src="https://github-readme-stats.vercel.app/api?username=timcreative&show_icons=true&include_all_commits=true&theme=cobalt&hide_border=true" alt="My github stats" /> 

<img align="center" src="https://github-readme-stats.vercel.app/api/top-langs/?username=timcreative&layout=compact&theme=cobalt&hide_border=true" />


Doa Mensyukuri Ni'mat

رَبِّ أَوْزِعْنِىٓ أَنْ أَشْكُرَ نِعْمَتَكَ ٱلَّتِىٓ أَنْعَمْتَ عَلَىَّ وَعَلَىٰ وَٰلِدَىَّ وَأَنْ أَعْمَلَ صَٰلِحًا تَرْضَىٰهُ وَأَدْخِلْنِى بِرَحْمَتِكَ فِى عِبَادِكَ ٱلصَّٰلِحِينَ


 
Ya Tuhanku, berilah aku ilham untuk tetap mensyukuri nikmat-Mu yang telah Engkau anugerahkan kepadaku dan kepada kedua orang ibu-bapakku dan untuk mengerjakan amal shalih yang Engkau ridhai, serta masukkanlah aku dengan rahmat-Mu ke dalam golongan hamba-hamba-Mu yang shalih


QS. Al-Naml 19


Keterangan :



Dijelaskan dalam Al-Qr'an bahwa ayat ini adalah doa Nabi Sulaiman kepada Allah SWT agar mendapatkan ilham untuk mensyukuri nikmat serta dimasukkan ke dalam golongan orang-orang yang beramal shalih di dunia hingga kemudian mendapatkan kebahagiaan di dunia dan akhirat.

# <summary><strong>Seeyou next time Terimakasih Sudah Berkunjung</summary>
Lifelong Learner, currently working as budagh kompeni.
<p align="left"> <img src="https://komarev.com/ghpvc/?username=goonesmile&label=Profile%20views&color=0e75b6&style=flat" alt="isrealodejobi" />
</p>

### <summary><strong>Tools:</strong></summary>
<p>
    <img src="https://img.shields.io/badge/Text%20Editor-Visual%20Studio%20Code-blue?&logo=visual%20studio%20code&logoColor=blue" />
</p>

### <summary><strong>Yosh!</strong></summary>
<p>
    - :keyboard: I’m currently learning Data Analytics. </br>
    - :speech_balloon: Ask me about anything.</br>
    - :mailbox: Kritik dan saran silahkan kirim ke: <a href="mailto: ruruhruhendi@gmail.com">Email me!</a>  </br>
    - :cloud: Pronouns: She/Her. </br>
    - :game_die: Drawing and writing are part of me. </br>
<p>
 
### <summary><strong>Let's connect!</strong></summary>
<a href="https://www.instagram.com/petoalam33/">
  <img align="left" alt="Goo's Instagram" width="20px" src="https://simpleicons.now.sh/instagram/495f7e" />

<a href="https://yours.com/">
  <img align="left" alt="Goo's Blog" width="20px" src="https://simpleicons.now.sh/blogger/495f7e" />
</a>
<img src="https://img.shields.io/badge/OS-MacOS-blue?&logo=apple" /> - MacOS
<img src="https://img.shields.io/badge/Code-Swift-blue?&logo=swift" /> - Swift
<img src="https://img.shields.io/badge/IDE-Xcode-blue?&logo=xcode" /> - IDE
<p>
    <img src="https://github-readme-stats.vercel.app/api?username=namaAnda&hide=contribs,prs&show_icons=true&hide_border=true&title_color=000" />
    <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=namaAnda&layout=compact" height=180 />
</p>


require 'sinatra/base'  # Use the Sinatra web framework
require 'octokit'       # Use the Octokit Ruby library to interact with GitHub's REST API
require 'dotenv/load'   # Manages environment variables
require 'json'          # Allows your app to manipulate JSON data
require 'openssl'       # Verifies the webhook signature
require 'jwt'           # Authenticates a GitHub App
require 'time'          # Gets ISO 8601 representation of a Time object
require 'logger'        # Logs debug statements

# This code is a Sinatra app, for two reasons:
#   1. Because the app will require a landing page for installation.
#   2. To easily handle webhook events.

class GHAapp < Sinatra::Application

  # Sets the port that's used when starting the web server.
  set :port, 3000
  set :bind, '0.0.0.0'

  # Expects the private key in PEM format. Converts the newlines.
  PRIVATE_KEY = OpenSSL::PKey::RSA.new(ENV['GITHUB_PRIVATE_KEY'].gsub('\n', "\n"))

  # Your registered app must have a webhook secret.
  # The secret is used to verify that webhooks are sent by GitHub.
  WEBHOOK_SECRET = ENV['GITHUB_WEBHOOK_SECRET']

  # The GitHub App's identifier (type integer).
  APP_IDENTIFIER = ENV['GITHUB_APP_IDENTIFIER']

  # Turn on Sinatra's verbose logging during development
  configure :development do
    set :logging, Logger::DEBUG
  end

  # Executed before each request to the `/event_handler` route
  before '/event_handler' do
    get_payload_request(request)
    verify_webhook_signature

    # If a repository name is provided in the webhook, validate that
    # it consists only of latin alphabetic characters, `-`, and `_`.
    unless @payload['repository'].nil?
      halt 400 if (@payload['repository']['name'] =~ /[0-9A-Za-z\-\_]+/).nil?
    end

    authenticate_app
    # Authenticate the app installation in order to run API operations
    authenticate_installation(@payload)
  end

  post '/event_handler' do

    # ADD EVENT HANDLING HERE #

    200 # success status
  end

  helpers do

    # ADD CREATE_CHECK_RUN HELPER METHOD HERE #

    # ADD INITIATE_CHECK_RUN HELPER METHOD HERE #

    # ADD CLONE_REPOSITORY HELPER METHOD HERE #

    # ADD TAKE_REQUESTED_ACTION HELPER METHOD HERE #

    # Saves the raw payload and converts the payload to JSON format
    def get_payload_request(request)
      # request.body is an IO or StringIO object
      # Rewind in case someone already read it
      request.body.rewind
      # The raw text of the body is required for webhook signature verification
      @payload_raw = request.body.read
      begin
        @payload = JSON.parse @payload_raw
      rescue => e
        fail  'Invalid JSON (#{e}): #{@payload_raw}'
      end
    end

    # Instantiate an Octokit client authenticated as a GitHub App.
    # GitHub App authentication requires that you construct a
    # JWT (https://jwt.io/introduction/) signed with the app's private key,
    # so GitHub can be sure that it came from the app and not altered by
    # a malicious third party.
    def authenticate_app
      payload = {
          # The time that this JWT was issued, _i.e._ now.
          iat: Time.now.to_i,

          # JWT expiration time (10 minute maximum)
          exp: Time.now.to_i + (10 * 60),

          # Your GitHub App's identifier number
          iss: APP_IDENTIFIER
      }

      # Cryptographically sign the JWT.
      jwt = JWT.encode(payload, PRIVATE_KEY, 'RS256')

      # Create the Octokit client, using the JWT as the auth token.
      @app_client ||= Octokit::Client.new(bearer_token: jwt)
    end

    # Instantiate an Octokit client, authenticated as an installation of a
    # GitHub App, to run API operations.
    def authenticate_installation(payload)
      @installation_id = payload['installation']['id']
      @installation_token = @app_client.create_app_installation_access_token(@installation_id)[:token]
      @installation_client = Octokit::Client.new(bearer_token: @installation_token)
    end

    # Check X-Hub-Signature to confirm that this webhook was generated by
    # GitHub, and not a malicious third party.
    #
    # GitHub uses the WEBHOOK_SECRET, registered to the GitHub App, to
    # create the hash signature sent in the `X-HUB-Signature` header of each
    # webhook. This code computes the expected hash signature and compares it to
    # the signature sent in the `X-HUB-Signature` header. If they don't match,
    # this request is an attack, and you should reject it. GitHub uses the HMAC
    # hexdigest to compute the signature. The `X-HUB-Signature` looks something
    # like this: 'sha1=123456'.
    def verify_webhook_signature
      their_signature_header = request.env['HTTP_X_HUB_SIGNATURE'] || 'sha1='
      method, their_digest = their_signature_header.split('=')
      our_digest = OpenSSL::HMAC.hexdigest(method, WEBHOOK_SECRET, @payload_raw)
      halt 401 unless their_digest == our_digest

      # The X-GITHUB-EVENT header provides the name of the event.
      # The action value indicates the which action triggered the event.
      logger.debug "---- received event #{request.env['HTTP_X_GITHUB_EVENT']}"
      logger.debug "----    action #{@payload['action']}" unless @payload['action'].nil?
    end

  end

  # Finally some logic to let us run this server directly from the command line,
  # or with Rack. Don't worry too much about this code. But, for the curious:
  # $0 is the executed file
  # __FILE__ is the current file
  # If they are the same—that is, we are running this file directly, call the
  # Sinatra run method
  run! if __FILE__ == $0
end
