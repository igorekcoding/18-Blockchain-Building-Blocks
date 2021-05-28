# 18-Blockchain-Building-Blocks
Homework 18
{
  "metadata": {
    "schemaVersion": "1.0",
    "importType": "LEX",
    "importFormat": "JSON"
  },
  "resource": {
    "name": "RoboAdvisor",
    "version": "3",
    "intents": [
      {
        "rejectionStatement": {
          "messages": [
            {
              "contentType": "PlainText",
              "content": "I will be pleased to assist you in the future."
            }
          ]
        },
        "name": "RecommendPortfolio",
        "version": "22",
        "fulfillmentActivity": {
          "type": "ReturnIntent"
        },
        "sampleUtterances": [
          "I would like to invest for my retirement",
          "I'm getting old what do you recommend me for retirement investment",
          "I want to invest for my retirement",
          "I'm worried about my retirement",
          "I want the best option to invest for my retirement",
          "I'm {age} and I want to invest for my retirement",
          "I'm {age} and I would like to invest for my retirement",
          "I want to invest for retire",
          "I want to save money for my retirement",
          "What do you recommend me for retirement"
        ],
        "slots": [
          {
            "sampleUtterances": [],
            "slotType": "AMAZON.NUMBER",
            "slotConstraint": "Required",
            "valueElicitationPrompt": {
              "messages": [
                {
                  "contentType": "PlainText",
                  "content": "How old are you?"
                }
              ],
              "maxAttempts": 2
            },
            "priority": 2,
            "name": "age"
          },
          {
            "sampleUtterances": [],
            "slotType": "AMAZON.US_FIRST_NAME",
            "slotConstraint": "Required",
            "valueElicitationPrompt": {
              "messages": [
                {
                  "contentType": "PlainText",
                  "content": "Thank you for trusting on me to help, could you please give me your name?"
                }
              ],
              "maxAttempts": 2
            },
            "priority": 1,
            "name": "firstName"
          },
          {
            "sampleUtterances": [],
            "slotType": "AMAZON.NUMBER",
            "slotConstraint": "Required",
            "valueElicitationPrompt": {
              "messages": [
                {
                  "contentType": "PlainText",
                  "content": "How much do you want to invest?"
                }
              ],
              "maxAttempts": 2
            },
            "priority": 3,
            "name": "investmentAmount"
          },
          {
            "sampleUtterances": [],
            "slotType": "RiskLevel",
            "slotTypeVersion": "1",
            "slotConstraint": "Required",
            "valueElicitationPrompt": {
              "messages": [
                {
                  "contentType": "PlainText",
                  "content": "What level of investment risk would you like to take?"
                },
                {
                  "contentType": "PlainText",
                  "content": "Risk Level"
                }
              ],
              "responseCard": "{\"version\":1,\"contentType\":\"application/vnd.amazonaws.card.generic\",\"genericAttachments\":[{\"imageUrl\":\"https://public-share-jarturomora.s3-us-west-2.amazonaws.com/none.png\",\"subTitle\":\"No risk at all\",\"title\":\"None\",\"buttons\":[{\"text\":\"None\",\"value\":\"None\"}]},{\"imageUrl\":\"https://public-share-jarturomora.s3-us-west-2.amazonaws.com/low.png\",\"subTitle\":\"Just a bit of risk\",\"title\":\"Very Low or Low\",\"buttons\":[{\"text\":\"Very Low\",\"value\":\"Very Low\"},{\"text\":\"Low\",\"value\":\"Low\"}]},{\"imageUrl\":\"https://public-share-jarturomora.s3-us-west-2.amazonaws.com/medium.png\",\"subTitle\":\"Let's start becoming wild\",\"title\":\"Medium\",\"buttons\":[{\"text\":\"Medium\",\"value\":\"Medium\"}]},{\"imageUrl\":\"https://public-share-jarturomora.s3-us-west-2.amazonaws.com/high.png\",\"subTitle\":\"I have no fear!\",\"title\":\"High or Very High\",\"buttons\":[{\"text\":\"High\",\"value\":\"High\"},{\"text\":\"Very High\",\"value\":\"Very High\"}]}]}",
              "maxAttempts": 2
            },
            "priority": 4,
            "name": "riskLevel"
          }
        ],
        "confirmationPrompt": {
          "messages": [
            {
              "contentType": "PlainText",
              "content": "Would you like me to search for the best investment portfolio for you now?"
            }
          ],
          "maxAttempts": 3
        }
      }
    ],
    "slotTypes": [
      {
        "description": "The available risk levels for investment",
        "name": "RiskLevel",
        "version": "1",
        "enumerationValues": [
          {
            "value": "High",
            "synonyms": [
              "high"
            ]
          },
          {
            "value": "Very Low",
            "synonyms": [
              "very low"
            ]
          },
          {
            "value": "Low",
            "synonyms": [
              "low"
            ]
          },
          {
            "value": "Medium",
            "synonyms": [
              "medium"
            ]
          },
          {
            "value": "Very High",
            "synonyms": [
              "very high"
            ]
          },
          {
            "value": "None",
            "synonyms": [
              "none"
            ]
          }
        ],
        "valueSelectionStrategy": "TOP_RESOLUTION"
      }
    ],
    "voiceId": "Matthew",
    "childDirected": false,
    "locale": "en-US",
    "idleSessionTTLInSeconds": 300,
    "clarificationPrompt": {
      "messages": [
        {
          "contentType": "PlainText",
          "content": "Sorry, can you please repeat that?"
        }
      ],
      "maxAttempts": 2
    },
    "abortStatement": {
      "messages": [
        {
          "contentType": "PlainText",
          "content": "Sorry, I could not understand. Goodbye."
        }
      ]
    }
  }
}
