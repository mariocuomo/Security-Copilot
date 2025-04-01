# Sentinel Daily Operations

## DESCRIPTION
This plugin aids in comprehending the recommended approach of integrating multiple related skills into a single plugin. The provided code sample demonstrates the combination of two skills to retrieve information from few Sentinel tables. You can further expand upon this example to extract additional details from custom tables etc.

---

## TYPE AND REQUIREMENTS
**TYPE**: KQL (Sentinel) <br>
**SOURCE**: _SigninLogs_ table <br>
**REQUIREMENTS**: Log Analytics Workspace with Sentinel enabled 

---

## SKILLS

<table>
  <tbody>
    <tr>
      <th>SkillName</th>
      <th align="center">Description</th>
      <th align="center">Parameters</th>
    </tr>
    <tr>
      <td><b>Top10FailedSigninsByApp</b></td>
      <td align="center">Get the top 10 Most Failed SignIn App in the last 24 hours.</td>
      <td>
      </td>
    </tr>
  </tbody>
</table>


---

## SAMPLE PROMPTS

- `« Retrieve the 10 apps with the most number of failed logins. Based on the App's name infer what they are used for with a simple description »`
- `« Retrieve the 10 apps with the most number of failed logins. Suggest me how to investigate. » `
---

## SCREENSHOTS
<div align="center">
  <img src="https://github.com/mariocuomo/Security-Copilot/blob/main/Images/Community%20Plugins/SentinelDailyOperations/FailedLoginDescription.png" width="700"> </img>
  <img src="https://github.com/mariocuomo/Security-Copilot/blob/main/Images/Community%20Plugins/SentinelDailyOperations/FailedLoginSuggestion.png" width="700"> </img>
</div>
