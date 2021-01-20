# facebook-ad-library-scraper (with modifications to the code)

*mod 1*
addition of search by funding entity (i.e. disclaimer) into .yaml and Python file

*mod 2*
line 95(ish) reading '#'impressions_max': ad['impressions']['upper_bound'],' gave some problems when retrieving ads, so I turned it into a comment (nullified it)

*mod 3*
adjusted search total from 5000 to 20000 ads, does run properly—slow sometimes, but can quit and re-run with no problems

*mod 4*
can only search by one FB Page ID at a time

*this is a forked repo of Max Woolf's (minimaxir) ad library scraper, find the original here: https://github.com/minimaxir/facebook-ad-library-scraper

# Very Detailed how-to (Instructions)
Max has done a great job writing a very thorough readme. Though everything makes sense to me, I recognize there are some parts that may be confusing to users who have little to no experience running any code. I have included a very detailed blurb on instructions below, so that everything makes sense to hopefully everyone.

*getting a Facebook user token*
1. to use this scraper, you need to verify your identity via Facebook's ad library API. Follow 'Step 1' here: https://www.facebook.com/ads/library/api/ This process involves getting physical snail mail after uploading a photo of personal identification, so it may take a couple days to a week or two. Identity verification took me a week and a half. 
 
a. You will also need to enable two-step verification if you haven't, already. I had my identity verified a half year ago, made a user token, found that it wasn't working in the scraper (error code in the shell was 10, I think), then found that my identity verification status had reverted from complete to incomplete because FB added a two-step verification requirement. Once I did that, all the tokens I generated worked with no problem. 
  
2. Your identity is confirmed and you can see a green check mark beside your country of residence under 'Running Ads About Social Issues, Elections or Politics' in Account Settings > Identity Confirmation. Now, go to https://developers.facebook.com/tools/explorer/, create a new app (doesn't matter what name you give it). You should be seeing the Graph API Explorer, and then click the 'Generate access token' button on the upper right hand quadrant of Your screen. Copy that string of letters and numbers.

3. Hover over 'Tools' on the top menu bar and click 'access token debugger' or go to https://developers.facebook.com/tools/debug/accesstoken/. Paste your access token, then click debug. Now copy that token, it is valid for 2 months now—your initial token would have been valid for a couple of hours. Store your token somewhere safe, treat it like a wallet: don't share it, don't let other people see it.

*using the ad library scraper*

4. Install pip (a genreally preferred installer program that you can use to install other things) via Terminal if you have not already. https://pip.pypa.io/en/stable/installing/ gives you the instructions you need.

5. Install the Python package requirements (this is akin to buying phone accessories for a phone to work, package requirements'requests' and 'tqdm' being the accessories and the ad library scraper .yaml and .py files being the phone). Do so via `pip`:

```sh
pip3 install requests tqdm
```

6. Download the zip file of the ad-library-scraper by clicking the green button on the top right hand quadrant of this branch page. 

7. Unzip the folder, open the folder now named facebook-ad-library-scraper-master, and open config.yaml in a text editor. I use Atom to read .yaml files. You can download it for free here: https://atom.io/.

8. Paste your token in line two, so that it reads the following (replace YOURACCESSTOKENHERE with your token): access_token: YOURACCESSTOKENHERE 

9. Likewise, you can fill in the fields after colons to specify what you are searching for. It should look like search_page_ids: ENTERPAGEIDHERE

a. you can find the ID of a Facebook page by going here: https://findmyfbid.in/

b. for instance, the page ID of GQ Magazine is 7962048097, so my line would read search_page_ids: 7962048097

10. Any line with a hashtag at the start means that whole line is a comment, you can turn lines of code into comment if you don't want them to run. You may want to omit the Page ID search query, but maybe use it another time. Add a hashtag at the start of that line for now, and remove it when you want to activate it again.

11. Now, open fb_ad_lib_scraper.py, which you can find in the unzipped folder. You can use IDLE to run this, IDLE is pre-installed if you have Python on your computer, I believe. 

12. On the top menu/task bar, click 'Run' and then, 'Run Module'. A shell should pop up, with a progress bar showing how many ads have been retrieved. The operation is done when you see >>> as the lowest/newest line in the shell. 

13. Your ad data is now saved under three file names in your unzipped folder. They are fb_ads.csv, fb_ads_regions.csv, fb_ads_demos.csv. You can read them using Excel or R or by uploading them to Google Sheets. Rename them so that your files are not overwritten when you run the code again with new parameters. The output is always stored in this folder (by the nature of the .py file) under these default names. 

## Creator

Max Woolf ([@minimaxir](https://minimaxir.com))

*Max's open-source projects are supported by his [Patreon](https://www.patreon.com/minimaxir) and [GitHub Sponsors](https://github.com/sponsors/minimaxir). If you found this project helpful, any monetary contributions to the Patreon are appreciated and will be put to good creative use.*

## License

MIT
