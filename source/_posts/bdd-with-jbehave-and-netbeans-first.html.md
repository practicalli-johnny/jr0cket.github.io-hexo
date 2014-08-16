title: BDD with JBehave and Netbeans - a first taste
date: 2010-02-28 16:00:00
categories: coding
tags: 
- bdd
- jbehave
- netbeans
---

{% img img-thumbnail http://issuetrackr.googlecode.com/svn-history/r105/trunk/issuetrackr/lib/jbehave-2.1/docs/images/jbehave-logo.png %} 

This is a quick overview of how I created a simple hello world example using JBehave and Netbeans, following the BDD development practices.

# Create a New Project

Create a new project in Netbeans `Ctrl-Shift-N`

Select a Java Application template (from the Java category) and call the project `HelloBDDWorld`

``` IReceiveAGreetingWhenILogin.java 
package org.jr0cket.scenarios;
import org.jbehave.scenario.Scenario;

public class IReceiveAGreetingWhenILogin extends Scenario {

    public IReceiveAGreetingWhenILogin(){
        super(new LoginSteps());
    }
}
```

``` LoginSteps.java

package org.jr0cket.scenarios;

import org.jbehave.scenario.steps.Steps;

class LoginSteps extends Steps {

    public LoginSteps() {   }
}

This exercise is based on the two minute tutorial on the JBehave site, with some added details for Netbeans and a couple of corrections.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

