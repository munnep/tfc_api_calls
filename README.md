# tfc_api_calls

You will do the following with this github repo

- create a workspace in TFC cloud
- create a team in TFC cloud
- associate the team with the workspace
- remove the team from the workspace
- remove the workspace

# How to

- Clone this repository
```
git clone https://github.com/munnep/tfc_api_calls.git
```
- Change directory into the cloned git folder
```
cd tf_api_calls
```
- export your token and organization to access the API and correct organization
```
export TOKEN=your_api_token
export ORGANIZATION=your_organization_name
```
- create a workspace. 
```
curl \
  --header "Authorization: Bearer $TOKEN" \
  --header "Content-Type: application/vnd.api+json" \
  --request POST \
  --data @create_workspace.json \
  https://app.terraform.io/api/v2/organizations/${ORGANIZATION}/workspaces

```
- workspace details
```
curl \
  --header "Authorization: Bearer $TOKEN" \
  --header "Content-Type: application/vnd.api+json" \
  https://app.terraform.io/api/v2/organizations/${ORGANIZATION}/workspaces/tfc_api_calls_test
```
- create a teams
```
curl \
  --header "Authorization: Bearer $TOKEN" \
  --header "Content-Type: application/vnd.api+json" \
  --request POST \
  --data @create_team.json \
  https://app.terraform.io/api/v2/organizations/${ORGANIZATION}/teams
```
- team details
```
curl \
  --header "Authorization: Bearer $TOKEN" \
  --header "Content-Type: application/vnd.api+json" \
  --request GET \
  https://app.terraform.io/api/v2/organizations/${ORGANIZATION}/teams
```
- associate a team with the workspace
change the values in ```team_associate.json``` with the workspace_id and team_id
```
curl \
  --header "Authorization: Bearer $TOKEN" \
  --header "Content-Type: application/vnd.api+json" \
  --request POST \
  --data @team_associate.json \
  https://app.terraform.io/api/v2/team-workspaces
```
- delete a workspace
```
curl \
  --header "Authorization: Bearer $TOKEN" \
  --header "Content-Type: application/vnd.api+json" \
  --request DELETE \
  https://app.terraform.io/api/v2/organizations/${ORGANIZATION}/workspaces/tfc_api_calls_test
```
- delete the team. Last value is team id
```
curl \
  --header "Authorization: Bearer $TOKEN" \
  --header "Content-Type: application/vnd.api+json" \
  --request DELETE \
  https://app.terraform.io/api/v2/teams/team-E2cR6LyCjjfYW8uU
```

