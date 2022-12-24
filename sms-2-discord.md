Profiles
    Profile: Anon
      Event: Received Text [ Type:Any Sender:C:ANY Content:* SIM Card:* MMS Body:* ]
    
    
    
    Enter Task: SMS
    Settings: Run Both Together
    
    <Webhook Link>
    A1: Variable Set [
          Name: %sim1_bot
          To: <Discord Webhook>
          Max Rounding Digits: 3
          Structure Output (JSON, etc): On ]
    
    A2: Parse/Format DateTime [
          Input Type: Now (Current Date And Time)
          Output Format: MMM dd yyyy | hh:mm a
          Output Format Separator: ,
          Output Offset Type: None ]
    
    A3: Variable Set [
          Name: %text
          To: %SMSRB
          Max Rounding Digits: 3
          Structure Output (JSON, etc): On ]
    
    A4: Variable Search Replace [
          Variable: %text
          Search: [\r\n]+
          Multi-Line: On
          Replace Matches: On
          Replace With: \\n\\n ]
    
    A5: HTTP Request [
          Method: POST
          URL: %sim1_bot
          Headers: content-type:application/json
          Body: {
            "content": ":incoming_envelope: Sender: **%SMSRN**\n:telephone: Sim: **%evtprm4**\n:timer: Time: **%formatted**",
            "embeds": [
              {
                "title": ":envelope: Message ",
                "description": "%text",
                "color": 837119
              }
            ]
          }
          Timeout (Seconds): 60
          Trust Any Certificate: On
          Structure Output (JSON, etc): On ]
    
    

    Profile: Anon
      Event: Received Text [ Type:SMS Sender:C:ANY Content:*verification*/*code*/*confirmation*/*setup*/*2FA*/*OTP* SIM Card:* MMS Body:* ]
    
    
    
    Enter Task: SMS-2FA
    Settings: Run Both Together
    
    <Webhook Link>
    A1: Variable Set [
          Name: %webhook
          To: <Discord Webhook>
          Max Rounding Digits: 3
          Structure Output (JSON, etc): On ]
    
    A2: Parse/Format DateTime [
          Input Type: Now (Current Date And Time)
          Output Format: MMM dd yyyy | hh:mm a
          Output Format Separator: ,
          Output Offset Type: None ]
    
    A3: Variable Set [
          Name: %text
          To: %SMSRB
          Max Rounding Digits: 3
          Structure Output (JSON, etc): On ]
    
    A4: Variable Search Replace [
          Variable: %text
          Search: [\r\n]+
          Multi-Line: On
          Replace Matches: On
          Replace With: \\n\\n ]
    
    A5: HTTP Request [
          Method: POST
          URL: %webhook
          Headers: content-type:application/json
          Body: {
            "content": ":incoming_envelope: Sender: **%SMSRN**\n:telephone: Sim: **%evtprm4**\n:timer: Time: **%formatted**",
            "embeds": [
              {
                "title": ":envelope: Message ",
                "description": "%text",
                "color": 837119
              }
            ]
          }
          Timeout (Seconds): 60
          Trust Any Certificate: On
          Structure Output (JSON, etc): On ]
    
    

Tasks
    Task: SMS
    Settings: Run Both Together
    
    <Webhook Link>
    A1: Variable Set [
          Name: %sim1_bot
          To: <Discord Webhook>
          Max Rounding Digits: 3
          Structure Output (JSON, etc): On ]
    
    A2: Parse/Format DateTime [
          Input Type: Now (Current Date And Time)
          Output Format: MMM dd yyyy | hh:mm a
          Output Format Separator: ,
          Output Offset Type: None ]
    
    A3: Variable Set [
          Name: %text
          To: %SMSRB
          Max Rounding Digits: 3
          Structure Output (JSON, etc): On ]
    
    A4: Variable Search Replace [
          Variable: %text
          Search: [\r\n]+
          Multi-Line: On
          Replace Matches: On
          Replace With: \\n\\n ]
    
    A5: HTTP Request [
          Method: POST
          URL: %sim1_bot
          Headers: content-type:application/json
          Body: {
            "content": ":incoming_envelope: Sender: **%SMSRN**\n:telephone: Sim: **%evtprm4**\n:timer: Time: **%formatted**",
            "embeds": [
              {
                "title": ":envelope: Message ",
                "description": "%text",
                "color": 837119
              }
            ]
          }
          Timeout (Seconds): 60
          Trust Any Certificate: On
          Structure Output (JSON, etc): On ]
    
    

    Task: Battery Bot
    Settings: Run Both Together
    
    <Webhook Link>
    A1: Variable Set [
          Name: %battery_bot
          To: <Discord Webhook>
          Max Rounding Digits: 3
          Structure Output (JSON, etc): On ]
    
    A2: Parse/Format DateTime [
          Input Type: Now (Current Date And Time)
          Output Format: MMM dd yyyy | hh:mm a
          Output Format Separator: ,
          Output Offset Type: None ]
    
    A3: HTTP Request [
          Method: POST
          URL: %battery_bot
          Headers: content-type:application/json
          Body: {
              "content": "Time: **%formatted**\nBattery Level: **%BATT%**"
          }
          Timeout (Seconds): 60
          Trust Any Certificate: On
          Structure Output (JSON, etc): On ]
    
    

    Task: SMS-2FA
    Settings: Run Both Together
    
    <Webhook Link>
    A1: Variable Set [
          Name: %webhook
          To: <Discord Webhook>
          Max Rounding Digits: 3
          Structure Output (JSON, etc): On ]
    
    A2: Parse/Format DateTime [
          Input Type: Now (Current Date And Time)
          Output Format: MMM dd yyyy | hh:mm a
          Output Format Separator: ,
          Output Offset Type: None ]
    
    A3: Variable Set [
          Name: %text
          To: %SMSRB
          Max Rounding Digits: 3
          Structure Output (JSON, etc): On ]
    
    A4: Variable Search Replace [
          Variable: %text
          Search: [\r\n]+
          Multi-Line: On
          Replace Matches: On
          Replace With: \\n\\n ]
    
    A5: HTTP Request [
          Method: POST
          URL: %webhook
          Headers: content-type:application/json
          Body: {
            "content": ":incoming_envelope: Sender: **%SMSRN**\n:telephone: Sim: **%evtprm4**\n:timer: Time: **%formatted**",
            "embeds": [
              {
                "title": ":envelope: Message ",
                "description": "%text",
                "color": 837119
              }
            ]
          }
          Timeout (Seconds): 60
          Trust Any Certificate: On
          Structure Output (JSON, etc): On ]
    
    