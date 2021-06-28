# Live Cricket Scorecard
## 



[Heroku Deployment](https://cricket-scorecard-2021.herokuapp.com/scorecard/36032)

This Flask app scrapes live scores , batting , bowling , winning team, playing eleven and Toss data from live ongoing matches in cricbuzz and returns it in a Json format.


## Features

- Get live batting and bowling scorecards (includes batsman dismissal mode, score, 6s 4s etc)
- Get toss data (Available after Toss is completed for a match)
- Get winning team and winning margin (Available after the match is over)
- Get Innings 1 and Innings 2 score 




## Tech

This app is built using:


- [Python](https://www.python.org/) - A Powerful and versatile programming language
- [Flask](https://pypi.org/project/Flask/) - Lightweight web application framework. for python





## Usage


To Get live scorecard of an ongoing match .

- Go to [cricbuzz](https://www.cricbuzz.com) and find your match
- Get match id from the URL of the match (a 5 digit no mentioned in the URL)
- Call the API url with the match id. For example:
```sh
https://cricket-scorecard-2021.herokuapp.com/scorecard/36032
```
- To get the live scorecard of IPL 2021 you don't need the match Id . Just enter the match no. For Example:

```sh
https://cricket-scorecard-2021.herokuapp.com/scorecard>ipl_match_no=21
```


## Sample Data

Request URL:
```sh
https://cricket-scorecard-2021.herokuapp.com/scorecard/36032
```

Data Received

```json
{
    "Innings1": [
                {
                    "Batsman": [
                                    {
                                    "balls": "25",
                                    "dismissal": "b A Shrubsole",
                                    "fours": "1",
                                    "name": "Smriti Mandhana",
                                    "runs": "10",
                                    "sixes": "0",
                                    "sr": "40.00"
                                    } 
                                ]
                },
                    {
                        "overs": "50",
                        "runs": 201,
                        "score": "201-8 (50 Ov)",
                        "team": "India Women",
                        "wickets": 8
                    }

    ],
    
    "playing_eleven": {
                       "England Women": [
                        "Lauren Winfield Hill",
                        "Tammy Beaumont",
                        "Heather Knight (c)",
                        "Natalie Sciver",
                        "Amy Ellen Jones (wk)",
                        "Sophia Dunkley",
                        "Katherine Brunt",
                        "Sarah Glenn",
                        "Sophie Ecclestone",
                        "Anya Shrubsole",
                        "Kate Cross"
                        ],
                        "India Women": [
                        "Smriti Mandhana",
                        "Shafali Verma",
                        "Punam Raut",
                        "Mithali Raj (c)",
                        "Harmanpreet Kaur",
                        "Deepti Sharma",
                        "Taniya Bhatia (wk)",
                        "Shikha Pandey",
                        "Jhulan Goswami",
                        "Pooja Vastrakar",
                        "Ekta Bisht"
                        ]
                    },
    "result": {
            "update": "england women won by 8 wkts",
            "winning_margin": "8 wkts",
            "winning_team": "england women"
        },
    "toss_result": {
    "chose_to": "bowl",
    "update": "England Women won the toss and opt to bowl",
    "winning_team": "England Women"
    }
}
```


## Development

Want to contribute? Great!

Please contact me @ rsumit123@gmail.com so that we can work on this together






## License

The rights to the data provided rests solely with cricbuzz and this data is only for personal use



