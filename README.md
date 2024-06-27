# SonarQube Maven Scan Action

This action scans a java maven project with SonarQube. Features:
- Does not require any change in the `pom.xml`, all configuration is read from `sonar-project.properties`
- Cache setup and compilation
- Optional restore of one or more artifacts to send additional info to SonarQube (e.g. coverage)
- Check the quality gate

## Inputs

- `github-token` *(Required)*: Token to access GitHub (needed to check the quality gate)
- `sonar-token` *(Required)*: Token to access SonarQube
- `sonar-host-url` *(Default to https://sonarcloud.io)*: Tells the scanner where SonarQube is hosted
- `working-directory` *(Default to root directory)*: The name of the working directory from which the scan is executed
- `java-version` *(Default 17)*: Java version used run the scans (JDK 17 is the minium required by SonarCloud)
- `restore-artifact-name<N>`, Where `<N>` is a number (1 to 6). Optional name of an artifact to be restored to send additional info to SonarQube (e.g. coverage reports)
- `restore-artifact-path<N>` *(Default to the `working-directory`)*: Path where `restore-artifact-name<N>` will be restored (relative to the working directory)'

## Example usage

```yaml
      - uses: javiertuya/sonarqube-action@main
        with: 
          github-token: ${{ secrets.GITHUB_TOKEN }}
          sonar-token: ${{ secrets.SONAR_TOKEN }}
          restore-artifact-name1: "test-coverage-files"
```
