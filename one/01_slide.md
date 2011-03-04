!SLIDE
# Quick Survey

!SLIDE 
# Lebowski:
## A SproutCore Testing Framework

!SLIDE 
# Disclaimers:

!SLIDE center
* ![center](centro_no.tagline.png)
* ![center](transis_no.tagline.png)

!SLIDE bullets
# _"Obviously you're not a golfer."_
* Not A JS Developer
* SC & Lebowski are both under heavy development

!SLIDE bullets
# _"And I'm talkin' about the Dude here"_
* Ruby Object Layer
* Built on top of selenium-client
* Exposes custom rspec matchers
* <tt>gem install lebowski</tt>

!SLIDE bullets
# _"Ve vant ze money, Lebowski"_
* Drag n' Drop
* Complex interactions
* SC layerID

!SLIDE smaller 
# examples/hello_world_spec.rb
    @@@ ruby
    App = MainApplication.new \
            :app_root_path => "/hello_world",
            :app_name => "HelloWorldApp",
            :browser => :firefox

    App.start do |app|
      app['isLoaded'] == true
    end

    # alias
    App.define_path 'group', 'mainPage.mainPane.groupView', View

!SLIDE code smaller
    @@@ ruby
    before(:all) do
      @label = App['group.label', 'SC.LabelView']
      @hello_button = App['group.helloButton', ButtonView]
      @world_button = App['#world-button', ButtonView]
    end

    it "will check that label has the value 'click a button'" do
      @label.should have_value /click a button/i
    end

!SLIDE code smaller

    @@@ cucumber
    Feature: Submitting an IO
    
      Scenario: Acceptance of an IO with no modifications
        Given I have a submitted a simple RFP to a tribune publisher
        When I log in to PCT2 as a production publisher
        And I review the submitted RFP  
        When I click the button 'Submit Placements'
        ...

!SLIDE center
# An now an offering to the demo gods...
* ![center](offering.jpg)

!SLIDE center
* ![center](sc-log.jpg)

!SLIDE smaller
# _"(Maude) You can imagine where it goes from here... (The Dude) He fixes the cable?"_
    @@@ ruby
    def wait_for_no_spinner
      spinz = "//div[@class='transis-spinner']"
      app.driver.wait_for_no_element spinz if agent.element? spinz
    end

    def wait_for_not_saving
      saving = "//label[contains(text(), 'Saving ...')]"
      app.driver.wait_for_no_element saving if agent.element? saving
    end

!SLIDE bullets
# _"This is what happens when you find a stranger in the alps!"_
* GridView
* Custom Views
* Sometimes need to drop into the selenium driver directly :-(

!SLIDE code
    @@@ ruby
    def fcuking_click_at(sel, pos = 0)
      agent.mouse_down_at sel, 0
      agent.mouse_up_at sel, 0
    end

!SLIDE center
* ![center](lebowski-issue.jpg)

!SLIDE bullets
# When to Use Lebowski
* Your interactions are stable
* You actually have time to invest
* An automated regression suite provides value

!SLIDE bullets
# Tools
* Firebug / Chrome Developer Tool
* [https://addons.mozilla.org/en-US/firefox/addon/sproutcore-pathpicker](https://addons.mozilla.org/en-US/firefox/addon/sproutcore-pathpicker)
* Cucumber, RSpec, minitest, etc.
* Your source code

!SLIDE bullets
# _"Yeah, well, that's just, like, your opinion, man."_
* Leverage VMs
* Headless & Parallel via Xvfb, Hydra, etc.

!SLIDE bullets
# Future
* SC Updates
* Selenium 2 and Firefox 4

!SLIDE bullets
# _"That rug really tied the room together"_
* Lebowski, Ki by @frozencanuck
* Under active development
* Generally works well, excellent documentation
* Sometimes have to break abstraction
* Fun work ahead

!SLIDE bullets
# Thanks!
* Jeffrey O'Dell, @umsondo
* [http://github.com/frozencanuck/lebowski](http://github.com/frozencanuck/lebowski)
* [http://lebowski-chi-sproutcore.heroku.com](http://lebowski-chi-sproutcore.heroku.com)
