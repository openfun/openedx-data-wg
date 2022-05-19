# Problems

For now, we only focus on server events.

## `problem_check`

### Mapping

|                                xAPI Key                               |                                                    Value                                                    |
|:---------------------------------------------------------------------:|:-----------------------------------------------------------------------------------------------------------:|
| Actor                                                                 |                                                                                                             |
| objectType                                                            | Agent                                                                                                       |
| account["homePage"]                                                   | <LMS_ROOT_URL>                                                                                              |
| account["name"]                                                       | <anonymized-user-id>                                                                                        |
| Verb                                                                  |                                                                                                             |
| id                                                                    | http://adlnet.gov/expapi/verbs/answered                                                                     |
| display["en-US"]                                                      | answered                                                                                                    |
| Object                                                                |                                                                                                             |
| id                                                                    | <LMS_ROOT_URL>/xblock/<data["problem_id"]>                                                                  |
| objectType                                                            | Activity                                                                                                    |
| definition["type"]                                                    | http://adlnet.gov/expapi/activities/question                                                                |
| definition["description"]                                             | <data["submission"][0]["question"]> if <data["submission"][0]["response_type"]> is not empty                |
| definition["interactionType"]                                         | Mapping of <data["submission"][0]["response_type"]> if <data["submission"][0][response_type"]> is not empty |
| Context                                                               |                                                                                                             |
| contextActivities["parent["objectType"]"]                             | Activity                                                                                                    |
| contextActivities["parent["id"]"]                                     | <LMS_ROOT_URL>/course/<data["course_id"]>                                                                   |
| contextActivities["parent["definition["type"]"]"]                     | http://adlnet.gov/expapi/activities/course                                                                  |
| contextActivities["parent["definition["name"]["en-US"]"]"]            | <name of course-run>                                                                                        |
| extensions["https://w3id.org/xapi/cmi5/context/extensions/sessionid"] | context["session"]                                                                                          |
| Results                                                               |                                                                                                             |
| success                                                               | TRUE if <data["success"]>=="correct" else FALSE                                                             |
| score["min"]                                                          | 0                                                                                                           |
| score["max"]                                                          | <data["max_grade"]>                                                                                         |
| score["raw"]                                                          | <data["grade"]>                                                                                             |
| score["scaled"]                                                       | <data["grade"]>/<data["max_grade"]>                                                                         |
| response                                                              | <data["submission"][0]["answer"]> if <data["submission"][0]["response_type"]> is not empty                  |

### Examples

#### edx

```json
{
    "context": {
        "accept_language": "en-US,en;q=0.9",
        "agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.116 Safari/537.36",
        "asides": {},
        "client_id": "667522224.1583394645",
        "course_id": "course-v1:edX+DemoX+Demo_Course",
        "course_user_tags": {},
        "event_source": "server",
        "host": "https://lms.example.org",
        "ip": "172.18.0.1",
        "module": {
            "display_name": "Checkboxes",
            "usage_key": "7599c6b50dd9"
        },
        "org_id": "edX",
        "page": "x_module",
        "path": "/courses/course-v1:edX+DemoX+Demo_Course/xblock/7599c6b50dd9/handler/xmodule_handler/problem_check",
        "referer": "https://lms.example.org/courses/course-v1:edX+DemoX+Demo_Course/courseware/8b66dcd2d6134eda9355089ece4f39f6/ef37eb3cf1724e38b7f88a9ce85a4842/?activate_block_id=block-v1%3AedX%2BDemoX%2BDemo_Course%2Btype%40sequential%2Bblock%40ef37eb3cf1724e38b7f88a9ce85a4842",
        "session": "3908784c-bf7a-445f-a887-0d1565baa06d",
        "user_id": 3,
        "username": "56255f3897599f377bf0e5bf072359fd"
    },
    "data": {
        "answers": {
            "3fc5461f86764ad7bdbdf6cbdde61e66_2_1": [
                "choice_0",
                "choice_2"
            ]
        },
        "attempts": 10,
        "correct_map": {
            "3fc5461f86764ad7bdbdf6cbdde61e66_2_1": {
                "answervariable": null,
                "correctness": "incorrect",
                "hint": "",
                "hintmode": null,
                "msg": "",
                "npoints": null,
                "queuestate": null
            }
        },
        "grade": 12,
        "max_grade": 12,
        "problem_id": "7599c6b50dd9",
        "state": {
            "correct_map": {
                "3fc5461f86764ad7bdbdf6cbdde61e66_2_1": {
                    "answervariable": null,
                    "correctness": "incorrect",
                    "hint": "",
                    "hintmode": null,
                    "msg": "",
                    "npoints": null,
                    "queuestate": null
                }
            },
            "done": true,
            "has_saved_answers": false,
            "input_state": {
                "3fc5461f86764ad7bdbdf6cbdde61e66_2_1": {}
            },
            "seed": 1,
            "student_answers": {
                "3fc5461f86764ad7bdbdf6cbdde61e66_2_1": [
                    "choice_0",
                    "choice_1",
                    "choice_2",
                    "choice_3"
                ]
            }
        },
        "submission": {
            "3fc5461f86764ad7bdbdf6cbdde61e66_2_1": {
                "answer": [
                    "a correct answer",
                    "an incorrect answer"
                ],
                "correct": false,
                "group_label": "",
                "input_type": "checkboxgroup",
                "question": "Add the question text, or prompt, here. This text is required.",
                "response_type": "choiceresponse",
                "variant": ""
            }
        },
        "success": "incorrect"
    },
    "name": "problem_check",
    "timestamp": "2022-05-23T03:42:01.323826+00:00"
}
```

#### xAPI

```json
{
  "id": "cb83227c-93db-43ae-9fc2-652c060f40be",
  "timestamp": "2022-05-23T03:42:01.323826+00:00",
  "actor": {
    "objectType": "Agent",
    "account": {
      "name": "56255f3897599f377bf0e5bf072359fd",
      "homePage": "https://lms.example.org"
    }
  },
  "verb": {
    "id": "http://adlnet.gov/expapi/verbs/answered",
    "display": {
      "en-US": "answered"
    }
  },
  "object": {
    "id": "https://lms.example.org/xblock/7599c6b50dd9",
    "objectType": "Activity",
    "definition": {
      "type": "http://adlnet.gov/expapi/activities/question",
      "description": {
        "en-US": "What is the meaning of life?"
      },
      "interactionType": "choice"
    }
  },
  "context": {
    "contextActivities": {
      "parent": [
        {
          "objectType": "Activity",
          "id": "https://lms.example.org/course/course-v1:ufr+mathematics+0001",
          "definition": {
            "type": "http://adlnet.gov/expapi/activities/course",
            "name": {
              "en-US": "Mathematics 101"
            }
          }
        }
      ]
    },
    "extensions": {
      "https://w3id.org/xapi/cmi5/context/extensions/sessionid": "3908784c-bf7a-445f-a887-0d1565baa06d",
    }
  },
  "results": {
    "success": true,
    "score": {
      "min": 0,
      "max": 12,
      "raw": 12,
      "scaled": 1.0
    },
    "response": "42"
  }
}
```
