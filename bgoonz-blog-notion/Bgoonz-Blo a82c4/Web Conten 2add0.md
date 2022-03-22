# Web Content Accessibility Guidelines (WCAG) 2.0

[https://www.w3.org/TR/2008/REC-WCAG20-20081211/#content-structure-separation](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#content-structure-separation)

**1.4.1 Use of Color:** Color is not used as the only visual means of conveying information, indicating an action, prompting a response, or distinguishing a visual element. (Level A)

*Note:* This success criterion addresses color perception specifically. Other forms of perception are covered in [Guideline 1.3](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#content-structure-separation) including programmatic access to color and other visual presentation coding.

**1.4.2 Audio Control:** If any audio on a Web page plays automatically for more than 3 seconds, either a [mechanism](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#mechanismdef) is available to pause or stop the audio, or a mechanism is available to control audio volume independently from the overall system volume level. (Level A)

*Note:* Since any content that does not meet this success criterion can interfere with a user's ability to use the whole page, all content on the Web page (whether or not it is used to meet other success criteria) must meet this success criterion. See [Conformance Requirement 5: Non-Interference](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#cc5).

## Principle 2: Operable - User interface components and navigation must be operable.

**2.1.1 Keyboard:** All [functionality](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#functiondef) of the content is operable through a [keyboard interface](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#keybrd-interfacedef) without requiring specific timings for individual keystrokes, except where the underlying function requires input that depends on the path of the user's movement and not just the endpoints. (Level A)

*Note 1:* This exception relates to the underlying function, not the input technique. For example, if using handwriting to enter text, the input technique (handwriting) requires path-dependent input but the underlying function (text input) does not.

*Note 2:* This does not forbid and should not discourage providing mouse input or other input methods in addition to keyboard operation.

**2.2.1 Timing Adjustable:** For each time limit that is set by the content, at least one of the following is true: (Level A)

- **Turn off:** The user is allowed to turn off the time limit before encountering it; or
- **Adjust:** The user is allowed to adjust the time limit before encountering it over a wide range that is at least ten times the length of the default setting; or
- **Extend:** The user is warned before time expires and given at least 20 seconds to extend the time limit with a simple action (for example, "press the space bar"), and the user is allowed to extend the time limit at least ten times; or
- **Real-time Exception:** The time limit is a required part of a real-time event (for example, an auction), and no alternative to the time limit is possible; or
- **Essential Exception:** The time limit is [essential](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#essentialdef) and extending it would invalidate the activity; or
- **20 Hour Exception:** The time limit is longer than 20 hours.

*Note:* This success criterion helps ensure that users can complete tasks without unexpected changes in content or context that are a result of a time limit. This success criterion should be considered in conjunction with  [Success Criterion 3.2.1](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#consistent-behavior-receive-focus), which puts limits on changes of content or context as a result of user action.

**2.2.2 Pause, Stop, Hide:** For moving, [blinking](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#blinksdef), scrolling, or auto-updating information, all of the following are true: (Level A)

- **Moving, blinking, scrolling:** For any moving, blinking or scrolling information that (1) starts automatically, (2) lasts more than five seconds, and (3) is presented in parallel with other content, there is a mechanism for the user to [pause](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#pauseddef), stop, or hide it unless the movement, blinking, or scrolling is part of an activity where it is [essential](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#essentialdef); and
- **Auto-updating:** For any auto-updating information that (1) starts automatically and (2) is presented in parallel with other content, there is a mechanism for the user to pause, stop, or hide it or to control the frequency of the update unless the auto-updating is part of an activity where it is essential.

*Note 1:* For requirements related to flickering or flashing content, refer to [Guideline 2.3](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#seizure).

*Note 2:* Since any content that does not meet this success criterion can interfere with a user's ability to use the whole page, all content on the Web page (whether it is used to meet other success criteria or not) must meet this success criterion. See [Conformance Requirement 5: Non-Interference](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#cc5).

*Note 3:* Content that is updated periodically by software or that is streamed to the user agent is not required to preserve or present information that is generated or received between the initiation of the pause and resuming presentation, as this may not be technically possible, and in many situations could be misleading to do so.

*Note 4:* An animation that occurs as part of a preload phase or similar situation can be considered essential if interaction cannot occur during that phase for all users and if not indicating progress could confuse users or cause them to think that content was frozen or broken.

## Principle 3: Understandable - Information and the operation of user interface must be understandable.

**3.1.5 Reading Level:** When text requires reading ability more advanced than the [lower secondary education level](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#lowseceddef) after removal of proper names and titles, [supplemental content](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#suppcontentdef), or a version that does not require reading ability more advanced than the lower secondary education level, is available. (Level AAA)

## Principle 4: Robust - Content must be robust enough that it can be interpreted reliably by a wide variety of user agents, including assistive technologies.

**4.1.1 Parsing:** In content implemented using markup languages, elements have complete start and end tags, elements are nested according to their specifications, elements do not contain duplicate attributes, and any IDs are unique, except where the specifications allow these features. (Level A)

*Note:* Start and end tags that are missing a critical character in their formation, such as a closing angle bracket or a mismatched attribute value quotation mark are not complete.

**4.1.2 Name, Role, Value:** For all [user interface components](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#user-interface-componentdef) (including but not limited to: form elements, links and components generated by scripts), the [name](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#namedef) and [role](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#roledef) can be [programmatically determined](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#programmaticallydetermineddef); states, properties, and values that can be set by the user can be [programmatically set](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#programmaticallysetdef); and notification of changes to these items is available to [user agents](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#useragentdef), including [assistive technologies](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#atdef). (Level A)

## Conformance

This section is [normative](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#normativedef).

This section lists requirements for [conformance](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#conformancedef) to WCAG 2.0. It also gives information about how to make conformance claims, which are optional. Finally, it describes what it means to be [accessibility supported](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#accessibility-supporteddef), since only accessibility-supported ways of using technologies can be [relied upon](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#reliedupondef) for conformance. [Understanding Conformance](http://www.w3.org/TR/UNDERSTANDING-WCAG20/conformance.html) includes further explanation of the accessibility-supported concept.

### Conformance Requirements

In order for a Web page to conform to WCAG 2.0, all of the following conformance requirements must be satisfied:

**1. Conformance Level:** One of the following levels of conformance is met in full.

- **Level A:** For Level A conformance (the minimum level of conformance), the [Web page](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#webpagedef) [satisfies](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#satisfiesdef) all the Level A Success Criteria, or a [conforming alternate version](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#conforming-alternate-versiondef) is provided.
- **Level AA:** For Level AA conformance, the Web page satisfies all the Level A and Level AA Success Criteria, or a Level AA conforming alternate version is provided.
- **Level AAA:** For Level AAA conformance, the Web page satisfies all the Level A, Level AA and Level AAA Success Criteria, or a Level AAA conforming alternate version is provided.

*Note 1:* Although conformance can only be achieved at the stated levels, authors are encouraged to report (in their claim) any progress toward meeting success criteria from all levels beyond the achieved level of conformance.

*Note 2:* It is not recommended that Level AAA conformance be required as a general policy for entire sites because it is not possible to satisfy all Level AAA Success Criteria for some content.

**4. Only Accessibility-Supported Ways of Using Technologies:** Only [accessibility-supported](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#accessibility-supporteddef) ways of using [technologies](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#technologydef) are [relied upon](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#reliedupondef) to satisfy the success criteria. Any information or functionality that is provided in a way that is not accessibility supported is also available in a way that is accessibility supported. (See [Understanding accessibility support](http://www.w3.org/TR/UNDERSTANDING-WCAG20/conformance.html#uc-accessibility-support-head).)

**5. Non-Interference:** If  [technologies](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#technologydef) are used in a way that is not [accessibility supported](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#accessibility-supporteddef), or if they are used in a non-conforming way, then they do not block the ability of users to access the rest of the page. In addition, the [Web page](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#webpagedef) as a whole continues to meet the conformance requirements under each of the following conditions:

1. when any technology that is not relied upon is turned off in a user agent, and
2. when any technology that is not relied upon is not supported by a user agent

In addition, the following success criteria apply to all content on the page, including content that is not otherwise relied upon to meet conformance, because failure to meet them could interfere with any use of the page:

- **1.4.2 - Audio Control**,
- **2.1.2 - No Keyboard Trap**,
- **2.3.1 - Three Flashes or Below Threshold**, and
- **2.2.2 - Pause, Stop, Hide**.

### Conformance Claims (Optional)

Conformance is defined only for [Web pages](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#webpagedef). However, a conformance claim may be made to cover one page, a series of pages, or multiple related Web pages.

### Required Components of a Conformance Claim

Conformance claims are **not required**. Authors can conform to WCAG 2.0 without making a claim. However, if a conformance claim is made, then the conformance claim **must** include the following information:

1. **Date** of the claim
2. **Guidelines title, version and URI**  "Web Content Accessibility Guidelines 2.0 at [http://www.w3.org/TR/2008/REC-WCAG20-20081211/](http://www.w3.org/TR/2008/REC-WCAG20-20081211/)"
3. **Conformance level** satisfied: (Level A, AA or AAA)
4. **A concise description of the Web pages**, such as a list of URIs for which the claim is made, including whether subdomains are included in the claim.
    
    *Note 1:* The Web pages may be described by list or by an expression that describes all of the URIs included in the claim.
    
    *Note 2:* Web-based products that do not have a URI prior to installation on the customer's Web site may have a statement that the product would conform when installed.
    

*Note:* If a conformance logo is used, it would constitute a claim and must be accompanied by the required components of a conformance claim listed above.

### Optional Components of a Conformance Claim

In addition to the required components of a conformance claim above, consider providing additional information to assist users. Recommended additional information includes:

- A list of success criteria beyond the level of conformance claimed that have been met. This information should be provided in a form that users can use, preferably machine-readable metadata.
- A list of user agents, including assistive technologies that were used to test the content.
- Information about any additional steps taken that go beyond the success criteria to enhance accessibility.
- A machine-readable metadata version of the list of specific technologies that are [relied upon](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#reliedupondef).
- A machine-readable metadata version of the conformance claim.

### Statement of Partial Conformance - Third Party Content

Sometimes, Web pages are created that will later have additional content added to them. For example, an email program, a blog, an article that allows users to add comments, or applications supporting user-contributed content. Another example would be a page, such as a portal or news site, composed of content aggregated from multiple contributors, or sites that automatically insert content from other sources over time, such as when advertisements are inserted dynamically.

In these cases, it is not possible to know at the time of original posting what the uncontrolled content of the pages will be. It is important to note that the uncontrolled content can affect the accessibility of the controlled content as well. Two options are available:

1. A determination of conformance can be made based on best knowledge. If a page of this type is monitored and repaired (non-conforming content is removed or brought into conformance) within two business days, then a determination or claim of conformance can be made since, except for errors in externally contributed content which are corrected or removed when encountered, the page conforms. No conformance claim can be made if it is not possible to monitor or correct non-conforming content;
    
    **OR**
    
2. A "statement of partial conformance" may be made that the page does not conform, but could conform if certain parts were removed. The form of that statement would be, "This page does not conform, but would conform to WCAG 2.0 at level X if the following parts from uncontrolled sources were removed." In addition, the following would also be true of uncontrolled content that is described in the statement of partial conformance:
    1. It is not content that is under the author's control.
    2. It is described in a way that users can identify (e.g., they cannot be described as "all parts that we do not control" unless they are clearly marked as such.)

### Statement of Partial Conformance - Language

A "statement of partial conformance due to language" may be made when the page does not conform, but would conform if [accessibility support](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#accessibility-supporteddef) existed for (all of) the language(s) used on the page. The form of that statement would be, "This page does not conform, but would conform to WCAG 2.0 at level X if accessibility support existed for the following language(s):"

## Appendix A: Glossary

This section is [normative](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#normativedef).

shortened form of a word, phrase, or name where the abbreviation has not become part of the language 
*Note 1:* This includes initialisms and acronyms where:
1.  **initialisms** are shortened forms of a name or phrase made from the initial letters of words or syllables contained in that name or phrase
2.  **acronyms** are abbreviated forms made from the initial letters or parts of other words (in a name or phrase) which may be pronounced as a word 
*Note 2:* Some companies have adopted what used to be an initialism as their company name. In these cases, the new name of the company is the letters (for example, Ecma) and the word is no longer considered an abbreviation.supported by users' [assistive technologies](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#atdef) as well as the accessibility features in browsers and other [user agents](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#useragentdef) 
To qualify as an accessibility-supported use of a Web content technology (or feature of a technology), both 1 and 2 must be satisfied for a Web content technology (or feature): 
1.  **The way that the [Web content technology](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#technologydef) is used must be supported by users' assistive technology (AT).** This means that the way that the technology is used has been tested for interoperability with users' assistive technology in the [human language(s)](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#human-langdef) of the content,
 **AND** 
2.  **The Web content technology must have accessibility-supported user agents that are available to users.** This means that at least one of the following four statements is true:
    1. The technology is supported natively in widely-distributed user agents that are also accessibility supported (such as HTML and CSS); 
 **OR** 
    2. The technology is supported in a widely-distributed plug-in that is also accessibility supported; 
 **OR** 
    3. The content is available in a closed environment, such as a university or corporate network, where the user agent required by the technology and used by the organization is also accessibility supported; 
 **OR** 
    4. The user agent(s) that support the technology are accessibility supported and are available for download or purchase in a way that:
        ▪ does not cost a person with a disability any more than a person without a disability **and**
        ▪ is as easy to find and obtain for a person with a disability as it is for a person without disabilities.
*Note 1:* The WCAG Working group and the W3C do not specify which or how much support by assistive technologies there must be for a particular use of a Web technology in order for it to be classified as accessibility supported. (See [Level of Assistive Technology Support Needed for "Accessibility Support"](http://www.w3.org/TR/UNDERSTANDING-WCAG20/conformance.html#uc-support-level-head).)
*Note 2:* Web technologies can be used in ways that are not accessibility supported as long as they are not [relied upon](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#reliedupondef) and the page as a whole meets the conformance requirements, including [Conformance Requirement 4: Only Accessibility-Supported Ways of Using Technologies](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#cc4) and [Conformance Requirement 5: Non-Interference](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#cc5), are met.
*Note 3:* When a [Web Technology](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#technologydef) is used in a way that is "accessibility supported," it does not imply that the entire technology or all uses of the technology are supported. Most technologies, including HTML, lack support for at least one feature or use. Pages conform to WCAG only if the uses of the technology that are accessibility supported can be relied upon to meet WCAG requirements.
*Note 4:* When citing Web content technologies that have multiple versions, the version(s) supported should be specified.
*Note 5:* One way for authors to locate uses of a technology that are accessibility supported would be to consult compilations of uses that are documented to be accessibility supported. (See [Understanding Accessibility-Supported Web Technology Uses](http://www.w3.org/TR/UNDERSTANDING-WCAG20/conformance.html#uc-documented-lists-head).) Authors, companies, technology vendors, or others may document accessibility-supported ways of using Web content technologies. However, all ways of using technologies in the documentation would need to meet the definition of accessibility-supported Web content technologies above. document including correctly sequenced text descriptions of time-based visual and auditory information and providing a means for achieving the outcomes of any time-based interaction the purpose cannot be determined from the link and all information of the Web page presented to the user simultaneously with the link (i.e., readers without disabilities would not know what a link would do until they activated it)
*Example:* The word guava in the following sentence "One of the notable exports is guava" is a link. The link could lead to a definition of guava, a chart listing the quantity of guava exported or a photograph of people harvesting guava. Until the link is activated, all readers are unsure and the person with a disability is not at any disadvantage.picture created by a spatial arrangement of characters or glyphs (typically from the 95 printable characters defined by ASCII). hardware and/or software that acts as a [user agent](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#useragentdef), or along with a mainstream user agent, to provide functionality to meet the requirements of users with disabilities that go beyond those offered by mainstream user agents 
*Note 1:*  functionality provided by assistive technology includes alternative presentations (e.g., as synthesized speech or magnified content), alternative input methods (e.g., voice), additional navigation or orientation mechanisms, and content transformations (e.g., to make tables more accessible). 
*Note 2:* Assistive technologies often communicate data and messages with mainstream user agents by using and monitoring APIs. 
*Note 3:* The distinction between mainstream user agents and assistive technologies is not absolute. Many mainstream user agents provide some features to assist individuals with disabilities. The basic difference is that mainstream user agents target broad and diverse audiences that usually include people with and without disabilities. Assistive technologies target narrowly defined populations of users with specific disabilities. The assistance provided by an assistive technology is more specific and appropriate to the needs of its target users. The mainstream user agent may provide important functionality to assistive technologies like retrieving Web content from program objects or parsing markup into identifiable bundles. 
*Example:* Assistive technologies that are important in the context of this document include the following:
• screen magnifiers, and other visual reading assistants, which are used by people with visual, perceptual and physical print disabilities to change text font, size, spacing, color, synchronization with speech, etc. in order to improve the visual readability of rendered text and images;
• screen readers, which are used by people who are blind to read textual information through synthesized speech or braille;
• text-to-speech software, which is used by some people with cognitive, language, and learning disabilities to convert text into synthetic speech;
• speech recognition software, which may be used by people who have some physical disabilities;
• alternative keyboards, which are used by people with certain physical disabilities to simulate the keyboard (including alternate keyboards that use head pointers, single switches, sip/puff and other special input devices.);
• alternative pointing devices, which are used by people with certain physical disabilities to simulate mouse pointing and button activations.narration added to the soundtrack to describe important visual details that cannot be understood from the main soundtrack alone a time-based presentation that contains only [audio](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#audiodef) (no [video](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#videodef) and no interaction)more than one sentence of textsynchronized visual and/or [text alternative](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#text-altdef) for both speech and non-speech audio information needed to understand the media content
*Note 1:* Captions are similar to dialogue-only subtitles except captions convey not only the content of spoken dialogue, but also equivalents for non-dialogue audio information needed to understand the program content, including sound effects, music, laughter, speaker identification and location.
*Note 2:* Closed Captions are equivalents that can be turned on and off with some players.
*Note 3:* Open Captions are any captions that cannot be turned off. For example, if the captions are visual equivalent [images of text](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#images-of-textdef) embedded in [video](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#videodef).
*Note 4:* Captions should not obscure or obstruct relevant information in the video.
*Note 5:* In some countries, captions are called subtitles.
*Note 6:*  [Audio descriptions](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#audiodescdef) can be, but do not need to be, captioned since they are descriptions of information that is already presented visually.major changes in the content of the [Web page](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#webpagedef) that, if made without user awareness, can disorient users who are not able to view the entire page simultaneously
*Note:* A change of content is not always a change of context. Changes in content, such as an expanding outline, dynamic menu, or a tab control do not necessarily change the context, unless they also change one of the above (e.g., focus).
*Example:* Opening a new window, moving focus to a different component, going to a new page (including anything that would look to a user as if they had moved to a new page) or significantly re-arranging the content of a page are examples of changes of context. satisfying all the requirements of a given standard, guideline or specification version that
1. conforms at the designated level, and
2.  is as up to date as the non-conforming content, and 
3. for which at least one of the following is true:
    1. the non-conforming version can only be reached from the conforming version, or
    2. the non-conforming version can only be reached from a conforming page that also provides a mechanism to reach the conforming version
*Note 1:* In this definition, "can only be reached" means that there is some mechanism, such as a conditional redirect, that prevents a user from "reaching" (loading) the non-conforming page unless the user had just come from the conforming version.
*Note 2:* The alternate version does not need to be matched page for page with the original (e.g., the conforming alternate version may consist of multiple pages).
*Note 3:* If multiple language versions are available, then conforming alternate versions are required for each language offered.
*Note 4:* Alternate versions may be provided to accommodate different technology environments or user groups. Each version should be as conformant as possible. One version would need to be fully conformant in order to meet [conformance requirement 1](http://www.w3.org/TR/2008/REC-WCAG20-20081211/#cc1).
*Note 5:* The conforming alternative version does not need to reside within the scope of conformance, or even on the same Web site, as long as it is as freely available as the non-conforming version. 
*Note 6:* Alternate versions should not be confused with [supplementary content](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#suppcontentdef), which support the original page and enhance comprehension.
*Note 7:* Setting user preferences within the content to produce a conforming version is an acceptable mechanism for reaching another version as long as the method used to set the preferences is accessibility supported. information and sensory experience to be communicated to the user by means of a [user agent](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#useragentdef), including code or markup that defines the content's [structure](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#structuredef), [presentation](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#presentationdef), and interactions (L1 + 0.05) / (L2 + 0.05), where
*Note 1:* Contrast ratios can range from 1 to 21 (commonly written 1:1 to 21:1).
*Note 2:* Because authors do not have control over user settings as to how text is rendered (for example font smoothing or anti-aliasing), the contrast ratio for text can be evaluated with anti-aliasing turned off.
*Note 3:* For the purpose of Success Criteria 1.4.3 and 1.4.6, contrast is measured with respect to the specified background over which the text is rendered in normal usage. If no background color is specified, then white is assumed. 
*Note 4:* Background color is the specified color of content over which the text is to be rendered in normal usage. It is a failure if no background color is specified when the text color is specified, because the user's default background color is unknown and cannot be evaluated for sufficient contrast. For the same reason, it is a failure if no text color is specified when a background color is specified. 
*Note 5:* When there is a border around the letter, the border can add contrast and would be used in calculating the contrast between the letter and its background. A narrow border around the letter would be used as the letter. A wide border around the letter that fills in the inner details of the letters acts as a halo and would be considered background.
*Note 6:* WCAG conformance should be evaluated for color pairs specified in the content that an author would expect to appear adjacent in typical presentation. Authors need not consider unusual presentations, such as color changes made by the user agent, except where caused by authors' code.any sequence where words and paragraphs are presented in an order that does not change the meaning of the content a sudden, unexpected situation or occurrence that requires immediate action to preserve health, safety, or property if removed, would fundamentally change the information or functionality of the content, **and** information and functionality cannot be achieved in another way that would conform a [flash](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#flash-def) or rapidly changing image sequence is below the threshold (i.e., content **passes**) if any of the following are true:
1. there are no more than three **general flashes** and / or no more than three **red flashes** within any one-second period; or
2. the combined area of flashes occurring concurrently occupies no more than a total of .006 steradians within any 10 degree visual field on the screen (25% of any 10 degree visual field on the screen) at typical viewing distance 
 where:
• A **general flash** is defined as a pair of opposing changes in [relative luminance](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#relativeluminancedef) of 10% or more of the maximum relative luminance where the relative luminance of the darker image is below 0.80; and where "a pair of opposing changes" is an increase followed by a decrease, or a decrease followed by an increase, and
• A **red flash** is defined as any pair of opposing transitions involving a saturated red.
 *Exception:* Flashing that is a fine, balanced, pattern such as white noise or an alternating checkerboard pattern with "squares" smaller than 0.1 degree (of visual field at typical viewing distance) on a side does not violate the thresholds.
*Note 1:* For general software or Web content, using a 341 x 256 pixel rectangle anywhere on the displayed screen area when the content is viewed at 1024 x 768 pixels will provide a good estimate of a 10 degree visual field for standard screen sizes and viewing distances (e.g., 15-17 inch screen at 22-26 inches). (Higher resolutions displays showing the same rendering of the content yield smaller and safer images so it is lower resolutions that are used to define the thresholds.)
*Note 2:* A transition is the change in relative luminance (or relative luminance/color for red flashing) between adjacent peaks and valleys in a plot of relative luminance (or relative luminance/color for red flashing) measurement against time. A flash consists of two opposing transitions. 
*Note 3:* The current working definition in the field for **"pair of opposing transitions involving a saturated red"** is where, for either or both states involved in each transition, R/(R+ G + B) >= 0.8, and the change in the value of (R-G-B)x320 is > 20 (negative values of (R-G-B)x320 are set to zero) for both transitions. R, G, B values range from 0-1 as specified in "relative luminance" definition. [[HARDING-BINNIE]](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#HARDING-BINNIE)
*Note 4:* Tools are available that will carry out analysis from video screen capture. However, no tool is necessary to evaluate for this condition if flashing is less than or equal to 3 flashes in any one second. Content automatically passes (see #1 and #2 above).phrase whose meaning cannot be deduced from the meaning of the individual words and the specific words cannot be changed without losing the meaning
*Example 1:* In English, "spilling the beans" means "revealing a secret." However, "knocking over the beans" or "spilling the vegetables" does not mean the same thing.
*Example 2:* In Japanese, the phrase "さじを投げる" literally translates into "he throws a spoon," but it means that there is nothing he can do and finally he gives up. 
*Example 3:* In Dutch, "Hij ging met de kippen op stok" literally translates into "He went to roost with the chickens," but it means that he went to bed early.interface used by software to obtain keystroke input
*Note 1:* A keyboard interface allows users to provide keystroke input to programs even if the native technology does not contain a keyboard.
*Example:* A touchscreen PDA has a keyboard interface built into its operating system as well as a connector for external keyboards. Applications on the PDA can use the interface to obtain keyboard input either from an external keyboard or from other applications that provide simulated keyboard output, such as handwriting interpreters or speech-to-text applications with "keyboard emulation" functionality.
*Note 2:* Operation of the application (or parts of the application) through a keyboard-operated mouse emulator, such as MouseKeys, does not qualify as operation through a keyboard interface because operation of the program is through its pointing device interface, not through its keyboard interface.with at least 18 point or 14 point bold or font size that would yield equivalent size for Chinese, Japanese and Korean (CJK) fonts 
*Note 1:* Fonts with extraordinarily thin strokes or unusual features and characteristics that reduce the familiarity of their letter forms are harder to read, especially at lower contrast levels.
*Note 2:* Font size is the size when the content is delivered. It does not include resizing that may be done by a user.
*Note 3:* The actual size of the character that a user sees is dependent both on the author-defined size and the user's display or user-agent settings. For many mainstream body text fonts, 14 and 18 point is roughly equivalent to 1.2 and 1.5 em or to 120% or 150% of the default size for body text (assuming that the body font is 100%), but authors would need to check this for the particular fonts in use. When fonts are defined in relative units, the actual point size is calculated by the user agent for display. The point size should be obtained from the user agent, or calculated based on font metrics as the user agent does, when evaluating this success criterion. Users who have low vision would be responsible for choosing appropriate settings. 
*Note 4:* When using text without specifying the font size, the smallest font size used on major browsers for unspecified text would be a reasonable size to assume for the font. If a level 1 heading is rendered in 14pt bold or higher on major browsers, then it would be reasonable to assume it is large text. Relative scaling can be calculated from the default sizes in a similar fashion. 
*Note 5:* The 18 and 14 point sizes for roman texts are taken from the minimum size for large print (14pt) and the larger standard font size (18pt). For other fonts such as CJK languages, the "equivalent" sizes would be the minimum large print size used for those languages and the next larger standard large print size.nature of the result obtained by activating a hyperlinkinformation captured from a real-world event and transmitted to the receiver with no more than a broadcast delay
*Note 1:* A broadcast delay is a short (usually automated) delay, for example used in order to give the broadcaster time to queue or censor the audio (or video) feed, but not sufficient to allow significant editing.
*Note 2:* If information is completely computer generated, it is not live.media that presents no more information than is already presented in text (directly or via text alternatives) 
*Note:* A media alternative for text is provided for those who benefit from alternate representations of text. Media alternatives for text may be audio-only, video-only (including sign-language video), or audio-video.navigated in the order defined for advancing focus (from one element to the next) using a [keyboard interface](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#keybrd-interfacedef) on the most common sized desktop/laptop display with the viewport maximized
*Note:* Since people generally keep their computers for several years, it is best not to rely on the latest desktop/laptop display resolutions but to consider the common desktop/laptop display resolutions over the course of several years when making this evaluation. stopped by user request and not resumed until requested by userseries of user actions where each action is required in order to complete an activity
*Example 1:* Successful use of a series of Web pages on a shopping site requires users to view alternative products, prices and offers, select products, submit an order, provide shipping information and provide payment information.
*Example 2:* An account registration page requires successful completion of a Turing test before the registration form can be accessed.programmatically determined (programmatically determinable)set by software using methods that are supported by user agents, including assistive technologies serving only an aesthetic purpose, providing no information, and having no functionalityevent that a) occurs at the same time as the viewing and b) is not completely generated by the content
*Example 1:* A Webcast of a live performance (occurs at the same time as the viewing and is not prerecorded).
*Example 2:* An on-line auction with people bidding (occurs at the same time as the viewing). 
*Example 3:* Live humans interacting in a virtual world using avatars (is not completely generated by the content and occurs at the same time as the viewing).  meaningful associations between distinct pieces of content the relative brightness of any point in a colorspace, normalized to 0 for darkest black and 1 for lightest white
*Note 1:* For the sRGB colorspace, the relative luminance of a color is defined as L = 0.2126 * **R** + 0.7152 * **G** + 0.0722 * **B** where **R**, **G** and **B** are defined as:
• if RsRGB <= 0.03928 then **R** = RsRGB/12.92 else **R** = ((RsRGB+0.055)/1.055) ^ 2.4
• if GsRGB <= 0.03928 then **G** = GsRGB/12.92 else **G** = ((GsRGB+0.055)/1.055) ^ 2.4
• if BsRGB <= 0.03928 then **B** = BsRGB/12.92 else **B** = ((BsRGB+0.055)/1.055) ^ 2.4
*Note 2:* Almost all systems used today to view Web content assume sRGB encoding. Unless it is known that another color space will be used to process and display the content, authors should evaluate using sRGB colorspace. If using other color spaces, see [Understanding Success Criterion 1.4.3](http://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-contrast.html).
*Note 3:* If dithering occurs after delivery, then the source color value is used. For colors that are dithered at the source, the average values of the colors that are dithered should be used (average R, average G, and average B). 
*Note 4:* Tools are available that automatically do the calculations when testing contrast and flash.
*Note 5:*  A [MathML version of the relative luminance definition](https://www.w3.org/TR/2008/REC-WCAG20-20081211/relative-luminance.xml) is available. relied upon (technologies that are)*Note:* Items are considered to be in the same relative order even if other items are inserted or removed from the original order. For example, expanding navigation menus may insert an additional level of detail or a secondary navigation section may be inserted into the reading order.the success criterion does not evaluate to 'false' when applied to the pagea language using combinations of movements of the hands and arms, facial expressions, or body positions to convey meaning [audio](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#audiodef) or [video](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#videodef) synchronized with another format for presenting information and/or with time-based interactive components, unless the media is a [media alternative for text](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#multimedia-alt-textdef) that is clearly labeled as such sequence of characters that can be [programmatically determined](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#programmaticallydetermineddef), where the sequence is expressing something in [human language](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#human-langdef) used in an unusual or restricted waywords used in such a way that requires users to know exactly which definition to apply in order to understand the content correctly
*Example:* The term "gig" means something different if it occurs in a discussion of music concerts than it does in article about computer hard drive space, but the appropriate definition can be determined from context. By contrast, the word "text" is used in a very specific way in WCAG 2.0, so a definition is supplied in the glossary.a time-based presentation that contains only [video](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#videodef) (no [audio](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#videodef) and no interaction)the font, size, color, and background can be set  a non-embedded resource obtained from a single URI using HTTP plus any other resources that are used in the rendering or intended to be rendered together with it by a [user agent](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#useragentdef) 
*Note 1:* Although any "other resources" would be rendered together with the primary resource, they would not necessarily be rendered simultaneously with each other.
*Note 2:* For the purposes of conformance with these guidelines, a resource must be "non-embedded" within the scope of conformance to be considered a Web page.
*Example 1:* A Web resource including all embedded images and media.
*Example 2:* A Web mail program built using Asynchronous JavaScript and XML (AJAX). The program lives entirely at http://example.com/mail, but includes an inbox, a contacts area and a calendar. Links or buttons are provided that cause the inbox, contacts, or calendar to display, but do not change the URI of the page as a whole.
*Example 3:* A customizable portal site, where users can choose content to display from a set of different content modules.
*Example 4:* When you enter "http://shopping.example.com/" in your browser, you enter a movie-like interactive shopping environment where you visually move around in a store dragging products off of the shelves around you and into a visual shopping cart in front of you. Clicking on a product causes it to be demonstrated with a specification sheet floating alongside. This might be a single-page Web site or just one page within a Web site.

## Appendix B: Acknowledgments

This section is [informative](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#informativedef).

This publication has been funded in part with Federal funds from the U.S. Department of Education, National Institute on Disability and Rehabilitation Research (NIDRR) under contract number ED05CO0039. The content of this publication does not necessarily reflect the views or policies of the U.S. Department of Education, nor does mention of trade names, commercial products, or organizations imply endorsement by the U.S. Government.

Additional information about participation in the Web Content Accessibility Guidelines Working Group (WCAG WG) can be found on the [Working Group home page](http://www.w3.org/WAI/GL/).

### Participants active in the WCAG WG at the time of publication

- Bruce Bailey (U.S. Access Board)
- Frederick Boland (NIST)
- Ben Caldwell (Trace R&D Center, University of Wisconsin)
- Sofia Celic (W3C Invited Expert)
- Michael Cooper (W3C)
- Roberto Ellero (International Webmasters Association / HTML Writers Guild)
- Bengt Farre (Rigab)
- Loretta Guarino Reid (Google)
- Katie Haritos-Shea
- Andrew Kirkpatrick (Adobe)
- Drew LaHart (IBM)
- Alex Li (SAP AG)
- David MacDonald (E-Ramp Inc.)
- Roberto Scano (International Webmasters Association / HTML Writers Guild)
- Cynthia Shelly (Microsoft)
- Andi Snow-Weaver (IBM)
- Christophe Strobbe (DocArch, K.U.Leuven)
- Gregg Vanderheiden (Trace R&D Center, University of Wisconsin)

### Other previously active WCAG WG participants and other contributors to WCAG 2.0

Shadi Abou-Zahra, Jim Allan, Jenae Andershonis, Avi Arditti, Aries Arditi, Mike Barta, Sandy Bartell, Kynn Bartlett, Marco Bertoni, Harvey Bingham, Chris Blouch, Paul Bohman, Patrice Bourlon, Judy Brewer, Andy Brown, Dick Brown, Doyle Burnett, Raven Calais, Tomas Caspers, Roberto Castaldo, Sambhavi Chandrashekar, Mike Cherim, Jonathan Chetwynd, Wendy Chisholm, Alan Chuter, David M Clark, Joe Clark, James Coltham, James Craig, Tom Croucher, Nir Dagan, Daniel Dardailler, Geoff Deering, Pete DeVasto, Don Evans, Neal Ewers, Steve Faulkner, Lainey Feingold, Alan J. Flavell, Nikolaos Floratos, Kentarou Fukuda, Miguel Garcia, P.J. Gardner, Greg Gay, Becky Gibson, Al Gilman, Kerstin Goldsmith, Michael Grade, Jon Gunderson, Emmanuelle Gutiérrez y Restrepo, Brian Hardy, Eric Hansen, Sean Hayes, Shawn Henry, Hans Hillen, Donovan Hipke, Bjoern Hoehrmann, Chris Hofstader, Yvette Hoitink, Carlos Iglesias, Ian Jacobs, Phill Jenkins, Jyotsna Kaki, Leonard R. Kasday, Kazuhito Kidachi, Ken Kipness, Marja-Riitta Koivunen, Preety Kumar, Gez Lemon, Chuck Letourneau, Scott Luebking, Tim Lacy, Jim Ley, William Loughborough, Greg Lowney, Luca Mascaro, Liam McGee, Jens Meiert, Niqui Merret, Alessandro Miele, Mathew J Mirabella, Charles McCathieNevile , Matt May, Marti McCuller, Sorcha Moore, Charles F. Munat, Robert Neff, Bruno von Niman, Tim Noonan, Sebastiano Nutarelli, Graham Oliver, Sean B. Palmer, Sailesh Panchang, Nigel Peck, Anne Pemberton, David Poehlman, Adam Victor Reed, Chris Ridpath, Lee Roberts, Gregory J. Rosmaita, Matthew Ross, Sharron Rush, Gian Sampson-Wild, Joel Sanda, Gordon Schantz, Lisa Seeman, John Slatin, Becky Smith, Jared Smith, Neil Soiffer, Jeanne Spellman, Mike Squillace, Michael Stenitzer, Jim Thatcher, Terry Thompson, Justin Thorp, Makoto Ueki, Eric Velleman, Dena Wainwright, Paul Walsch, Takayuki Watanabe, Jason White.

## Appendix C: References

This section is [informative](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#informativedef).

Web Content Accessibility Guidelines 1.0, G. Vanderheiden, W. Chisholm, I. Jacobs, Editors, W3C Recommendation, 5 May 1999, http://www.w3.org/TR/1999/WAI-WEBCONTENT-19990505/. The latest version of WCAG 1.0 is available at [http://www.w3.org/TR/WAI-WEBCONTENT/](http://www.w3.org/TR/WAI-WEBCONTENT/).
