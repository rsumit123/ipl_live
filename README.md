# Live Cricket Scorecard

This Flask app scrapes live scores, batting, bowling, winning team, playing eleven, toss data and ball-by-ball commentary from live/completed matches on Cricbuzz and returns it in JSON format.

> **Note:** The v1 endpoints use Cricbuzz's old internal HTML API (`/api/html/cricket-scorecard`) which is now defunct. Use the **v2 endpoints** for all new integrations.


## Features

- Get live batting and bowling scorecards (includes batsman dismissal, score, 6s, 4s, SR, etc.)
- Get toss data (available after toss is completed)
- Get winning team and winning margin (available after match is over)
- Get Innings 1 and Innings 2 scores
- **[v2]** Ball-by-ball commentary for the most recent ~2 overs of a live match


## Tech

This app is built using:

- [Python](https://www.python.org/) - A powerful and versatile programming language
- [Flask](https://pypi.org/project/Flask/) - Lightweight web application framework for Python


## Endpoints

### v2 (recommended)

#### `GET /v2/scorecard/<match_id>`
Returns the full scorecard for any Cricbuzz match (live or completed).

```sh
GET /v2/scorecard/149618
```

#### `GET /v2/commentary/<match_id>`
Returns ball-by-ball commentary for the most recent ~2 overs. Best used for live matches.

```sh
GET /v2/commentary/149684
```

---

### v1 (legacy — defunct)

#### `GET /scorecard/<match_id>`
#### `GET /scorecard?ipl_match_no=<n>`

These endpoints rely on a Cricbuzz API that is no longer active and will return errors.

---

## Usage

- Go to [cricbuzz.com](https://www.cricbuzz.com) and find your match
- Get the match ID from the URL (the numeric ID in the URL, e.g. `149618`)
- Call the v2 API with the match ID:

```sh
GET /v2/scorecard/149618
GET /v2/commentary/149618
```

## Sample Response — `/v2/scorecard/<match_id>`

```json
{
    "Innings1": [
        {
            "Batsman": [
                {
                    "balls": "9",
                    "dismissal": "c Phil Salt b Jacob Duffy",
                    "fours": "2",
                    "name": "Travis Head",
                    "runs": "11",
                    "sixes": "0",
                    "sr": "122.22"
                }
            ]
        },
        {
            "Bowlers": [
                {
                    "economy": "5.5",
                    "maidens": "0",
                    "name": "Jacob Duffy",
                    "overs": "4",
                    "runs": "22",
                    "wicket": "3"
                }
            ]
        },
        {
            "overs": "20",
            "runs": 201,
            "score": "201-9 (20 Ov)",
            "team": "Sunrisers Hyderabad",
            "wickets": 9
        }
    ],
    "Innings2": ["..."],
    "playing_eleven": {
        "Sunrisers Hyderabad": ["Travis Head", "Abhishek Sharma", "..."],
        "Royal Challengers Bengaluru": ["Phil Salt", "Virat Kohli", "..."]
    },
    "result": {
        "update": "royal challengers bengaluru won by 6 wkts",
        "winning_margin": "6 wkts",
        "winning_team": "Royal Challengers Bengaluru"
    },
    "toss_result": {
        "chose_to": "bowling",
        "update": "Royal Challengers Bengaluru won the toss and opt to bowling",
        "winning_team": "Royal Challengers Bengaluru"
    }
}
```

## Sample Response — `/v2/commentary/<match_id>`

```json
{
    "match_id": "149684",
    "total_balls": 14,
    "commentary": [
        {
            "over": 11,
            "ball": 5,
            "ball_metric": 11.5,
            "innings_id": 2,
            "event": "wicket",
            "comm_text": "Anshul Kamboj to Cooper Connolly, out Caught by Matt Henry!! A juicy full toss around off, Connolly looks to loft it down the ground and gets it high on the bat, the ball flies to long-off where Henry comes in and takes a simple catch. Cooper Connolly c Matt Henry b Anshul Kamboj 36(22) [4s-6]",
            "comm_text_html": "Anshul Kamboj to Cooper Connolly, <b>out</b> Caught by Matt Henry!! ...",
            "batsman": "Cooper Connolly",
            "bowler": "Anshul Kamboj",
            "timestamp": 1775236473164
        }
    ]
}
```


## Development

Want to contribute? Great!

Please contact me @ rsumit123@gmail.com so that we can work on this together


## License

The rights to the data provided rests solely with cricbuzz and this data is only for personal use
