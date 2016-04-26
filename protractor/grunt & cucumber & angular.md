# Setup

* clone project https://github.com/danwellman/notes/
* Finished source code: 
https://github.com/kurorido/protractor-cucumber-practice

* install 
```
npm install
npm install --save-dev cucumber protractor protractor-cucumber-framework chai chai-as-promised grunt-protractor-runner
npm intall -g protractor
```
安裝後會有 webdriver-manager

* update & start selenium driver
```
webdriver-manager update
webdriver-manager start
```

* Add grunt-tasks protractor.js
```
module.exports = {
    all: {
        options: {
            configFile: 'test/e2e/conf.js'
        }
    }
};
```

* Add test/e2e/conf.js file
```
exports.config = {
    framework: 'custom',
    frameworkPath: '../../node_modules/protractor-cucumber-framework',
    seleniumAddress: 'http://localhost:4444/wd/hub',
    specs: 'features/**/*.feature',
    cucumberOpts: {
        require: 'steps/**/*.steps.js',
        format: 'pretty'
    }
};
```

* Write Features
```
Feature: Save Button
    As a user of the application
    I would like to be able to save my notes

Scenario: Enabling Save Button
    Given I am using the app
    When I focus the textarea
        And I begin typing
    Then the save button is enabled
```

* Write Steps
```
var chai = require('chai');

module.exports = function() {
   this.Given(/^I am using the app$/, function (callback) {
     browser.get('http://localhost:8080/app/app.html').then(function() {
        callback();
     });
   });

   this.When(/^I focus the textarea$/, function (callback) {
     var textarea = element(by.css('textarea'));
     textarea.click().then(function() {
        callback();
     });
   });

   this.When(/^I begin typing$/, function (callback) {
     var textarea = element(by.css('textarea'));
     textarea.sendKeys('a').then(function () {
        callback();
     });
   });

   this.Then(/^the save button is enabled$/, function (callback) {
     var button = element(by.id('save'));
     button.isEnabled().then(function (enabledState) {
        chai.expect(enabledState).to.equals(true);
        callback();
     });
   });

};
```

* Run

```
grunt protractor
```



