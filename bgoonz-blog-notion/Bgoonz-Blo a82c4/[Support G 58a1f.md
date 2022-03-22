# [Support Guide] Frequently encountered problems during builds - Support / Support Guides - Netlify Support Forums

[https://answers.netlify.com/t/support-guide-frequently-encountered-problems-during-builds/213/3](https://answers.netlify.com/t/support-guide-frequently-encountered-problems-during-builds/213/3)

![%5BSupport%20G%2058a1f/249f93954af7d92ffcc7bedf1a87586e136fa4fc.png](%5BSupport%20G%2058a1f/249f93954af7d92ffcc7bedf1a87586e136fa4fc.png)

It would be useful if your FAQ above included the following information:

The final part of the build after it gives the number of files to upload can time out without completing if you have many tens of thousands of files. However, some of the files (typically a few tens of thousands) will have been processed, so if you re-run the same build you fill find that there are now fewer files to upload. Repeating build re-runs will eventually get all your files uploaded and the build will complete.

However, there is a second "uploading" stage after the build has completed that can easily take several hours for the first deployment for a site with many tens of thousands of files. Once that deployment has completed, subsequent deployments (both build and subsequent upload stage) should be fairly fast (a few minutes) so long as there aren't too many unchanged files.

Hi,
 I have a Gatsby site deployed on Netlify but I am running into an issue with my latest deploy. After reading the above & Netlify's docs, I believe I am encountering #7 - post processing issue.
 The fail message says: ‘Deploy processing failed after 5 attempts.'

I have tried the following:

1. Added `CI='' npm run build` as build command to bypass warning errors
2. Disabled Asset optimization
3. Downloaded Netlify CLI and ran `netlify dev`, `netlify build` (both successful)
4. Ran `DEBUG=* netlify deploy` and am seeing: "error_message": "Deploy processing failed after 5 attempts".

Can you please advise on next steps to debug this issue? I have not been able to deploy my site since yesterday.

Thanks!

Hi [@hrishikesh](https://answers.netlify.com/u/hrishikesh), I am using Netlify forms and have multiple forms on one page. I realized the deploy is successful when I only have one form.
 I am setting each form name, id, and fields dynamically (using GraphQL, Gatsby, Contenful). Here is my form's code:

```
<form
name={form.title}
method="POST"
data-netlify="true"
id={form.slug}
>
<div
  className="input_padding_bottom  mt-36"
  data-delay="100"
>
  <input
    name={form.formField1}
    type="text"
    id={form.formField1}
    size="30"
    placeholder={form.formField1}
    required
  />
  <label
    className="input_label"
    htmlFor={form.formField1}
  ></label>
</div>

<div
  className="input_padding_bottom "
  data-delay="150"
>
  <input
    name={form.formField2}
    type="text"
    id={form.formField2}
    size="30"
    placeholder={form.formField2}
    required
  />
  <label
    className="input_label"
    htmlFor={form.formField2}
  ></label>
</div>
<div
  className="input_padding_bottom "
  data-delay="150"
>
  <input
    name={form.formField3}
    type="text"
    id={form.formField3}
    size="30"
    placeholder={form.formField3}
    required
  />
  <label
    className="input_label"
    htmlFor={form.formField3}
  ></label>
</div>
<div className="" data-delay="100">
  <textarea
    name={form.formField4}
    cols="40"
    rows="4"
    id={form.formField4}
    placeholder={form.formField4}
  ></textarea>
  <label
    className="input_label slow"
    htmlFor={form.formField4}
  ></label>
</div>
<button
type="submit"
className="send_message"
id="submit"
>
{form.cta}
</button>
</form>

```

your view may look a bit different, but from the main forums page at [answers.netlify.com](http://answers.netlify.com/) please just select "new topic" and give us as much information as possible:

![%5BSupport%20G%2058a1f/63728689b33a9d292fd89a466d963056d85a365f_2_1380x488.jpeg](%5BSupport%20G%2058a1f/63728689b33a9d292fd89a466d963056d85a365f_2_1380x488.jpeg)
