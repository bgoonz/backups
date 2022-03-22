# WAI-ARIA Authoring Practices 1.1

[https://www.w3.org/TR/wai-aria-practices-1.1/](https://www.w3.org/TR/wai-aria-practices-1.1/)

## Abstract

This document provides readers with an understanding of how to use [WAI-ARIA 1.1](https://www.w3.org/TR/wai-aria-1.1/) [[WAI-ARIA](https://www.w3.org/TR/wai-aria-practices-1.1/#bib-wai-aria)] to create accessible rich internet applications. It describes considerations that might not be evident to most authors from the WAI-ARIA specification alone and recommends approaches to make widgets, navigation, and behaviors accessible using WAI-ARIA roles, states, and properties. This document is directed primarily to Web application developers, but the guidance is also useful for user agent and assistive technology developers.

This document is part of the WAI-ARIA suite described in the [WAI-ARIA Overview](https://www.w3.org/WAI/intro/aria.php).

## Status of This Document

*This section describes the status of this document at the time of its publication. Other documents may supersede this document. A list of current W3C publications and the latest revision of this technical report can be found in the [W3C technical reports index](https://www.w3.org/TR/) at https://www.w3.org/TR/.*

This is the WAI-ARIA Authoring Practices 1.1 [Working Group Note](https://www.w3.org/2018/Process-20180201/#WGNote) by the [Accessible Rich Internet Applications Working Group](https://www.w3.org/WAI/ARIA/). It supports the [Accessible Rich Internet Applications 1.1 W3C Recommendation](https://www.w3.org/TR/wai-aria-1.1/) [[wai-aria-1.1](https://www.w3.org/TR/wai-aria-practices-1.1/#bib-wai-aria)], providing detailed advice and examples beyond what would be appropriate to a technical specification but which are important to understand the specification.

WAI-ARIA Authoring Practices 1.1 was previously published as a Working Group Note in December 2017, to accompany the WAI-ARIA 1.1 Recommendation, and was republished in July 2018 and February 2019 with additional design pattern and examples, quality improvements, and improveed support for WAI-ARIA 1.1. Details of changes are described in the [change log](https://www.w3.org/TR/wai-aria-practices-1.1/#change_log). Separately, [WAI-ARIA Authoring Practices 1.2](https://www.w3.org/TR/wai-aria-practices-1.2/) includes the improvements in this document plus additional features specific to [WAI-ARIA 1.2](https://www.w3.org/TR/wai-aria-1.2/).

To comment, [file an issue in the W3C ARIA Practices GitHub repository](https://github.com/w3c/aria-practices/issues/), or if that is not possible, send email to [public-aria@w3.org](mailto:public-aria@w3.org?subject=Comment%20on%20WAI-ARIA%20Practices%201.1) ([comment archive](http://lists.w3.org/Archives/Public/public-aria/)).

This document was published by the [Accessible Rich Internet Applications Working Group](https://www.w3.org/WAI/ARIA/) as a Working Group Note.

Comments regarding this document are welcome. Please send them to [public-aria@w3.org](mailto:public-aria@w3.org) ([archives](https://lists.w3.org/Archives/Public/public-aria/)).

Publication as a Working Group Note does not imply endorsement by the W3C Membership. This is a draft document and may be updated, replaced or obsoleted by other documents at any time. It is inappropriate to cite this document as other than work in progress.

This document was produced by a group operating under the [W3C Patent Policy](https://www.w3.org/Consortium/Patent-Policy/).

This document is governed by the [1 March 2019 W3C Process Document](https://www.w3.org/2019/Process-20190301/).

## 1. Introduction

This section is *informative.*

WAI-ARIA Authoring Practices is a guide for understanding how to use [WAI-ARIA 1.1](https://www.w3.org/TR/wai-aria-1.1/) to create an accessible Rich Internet Application. It provides guidance on the appropriate application of WAI-ARIA, describes recommended WAI-ARIA usage patterns, and explains concepts behind them.

Languages used to create rich and dynamic web sites, e.g., HTML, JavaScript, CSS, and SVG, do not natively include all the features required to make sites usable by people who use assistive technologies (AT) or who rely on keyboard navigation. The W3C Web Accessibility Initiative's (WAI) Accessible Rich Internet Applications working group (ARIA WG) is addressing these deficiencies through several W3C standards efforts. The [WAI-ARIA Overview](https://www.w3.org/WAI/intro/aria.php) provides additional background on WAI-ARIA, summarizes those efforts, and lists the other documents included in the WAI-ARIA suite.

After a brief Read Me First section, the guide begins with ARIA implementation patterns for common widgets that both enumerate expected behaviors and demonstrate those behaviors with working code. The implementation patterns and examples refer to detailed explanations of supporting concepts in subsequent guidance sections. The guidance sections cover more general topics such as use of ARIA landmarks, practices for keyboard interfaces, grid and table properties, and the effects of role `presentation`.