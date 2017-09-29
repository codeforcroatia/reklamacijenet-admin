---
layout: post
title:  "Upravljanje predmetima"
date:   2017-09-29
---

Alaveteli makes it easy for a user to make a request. As an administrator, there are some things about that request you can change once it’s been created.

A request is automatically created when a user submits and (where necessary) confirms it. Alaveteli sends it to the authority responsible and handles any responses. Usually this process runs without needing any intervention from an administrator. But sometimes you’ll want to change some aspect of the request, or the way Alaveteli is handling it.

What state is the request in?#

Every request moves through a series of states, indicating its progress. Usually a new request will be in the waiting_response state until something happens to change that — for example, a response is received.

However, states can’t always be set automatically, because they require a decision to be made on what kind of answer the authority provided in the response. For states like this, Alaveteli invites the original requester to describe it — for example, when a response is received they can change the state to successful, partially_successful or not_held (if the authority replied to say they don’t have the information requested).

If a request has been waiting for over three weeks for the original requester to describe it but has still not been described, Alaveteli lets anyone classify it.
Internally, Alaveteli does not just record the “described state” of a request, but also notices if anything has happened since it was last described and sets its “awaiting description” status appropriately.

Old requests (by default, 6+ months without activity)#

If there is no activity on a request for some months (by default six), Alaveteli automatically changes that request’s Allow new responses from… setting to authority_only. Any responses will be rejected unless they are from the authority to which the request was originally made.

If a further number of months pass with no activity, that is, by default, if a year has passed without any updates, the request’s Allow new responses from… setting becomes nobody. All responses to this request will be rejected. The request is effectively closed.

By default, any rejected responses will be bounced with a message that explains that the request has been closed because it is old, with a suggestion that the sender can email your site’s administrators directly.

You can can stop this behaviour by changing the Allow new responses from… setting back to normal at any time. Alternatively, you can change the way rejected messages are handled (for example, sending such responses to the holding pen instead of bouncing them) with the request’s Handle rejected responses setting.

See changing things about a request below for how to change these settings.

You can change the number of months it takes for responses to be restricted, and then rejected, by changing the RESTRICT_NEW_RESPONSES_ON_OLD_REQUESTS_AFTER_MONTHS setting in the config.

Changing things about a request#

To change any of these settings, go to the admin interface, click on Requests, then click on the title of the request you want to affect. Click the Edit metadata button.

What you can change	Details
Title	The title is shown on the request’s page, but is also used in the URL (the text is changed to lower case, punctuation is removed and, if necessary, a number is added for disambiguation — this is called the “slug”).
Note that changing the title changes the URL, because the slug changes — this means any links to the old URL will no longer work, and will return a 404 (file not found) error.

Who can see it?	Change the Prominence setting to one of:
normal
backpage: request can be seen by anyone (by visiting its URL, for example) but does not appear in lists, or search results
requester_only: request only visible to the person who made the request
hidden: request is never shown (except to administrators)

Who can respond?	The Allow new responses from... setting can be one of:
anybody
authority_only: responses are allowed if they come from the authority to which the request was sent, or from any domain from which a a response has already been accepted
nobody: no responses are allowed on this request
Any response from a sender who has been disallowed by this setting will be rejected (see next entry).

This setting may change automatically when the request gets old.

What happens to rejected responses?	The Handle rejected responses... setting specificies what happens to responses that are not allowed (see previous entry):
bounce: responses are sent back to their sender
holding pen: responses are put in the holding pen for an administrator to deal with
blackhole: responses are destroyed by being sent to a black hole
What state is it in?	See more about request states, which can be customised for your installation.
You can force the state of the request by choosing it explicitly. Change the Described state setting.

You may also need to set Awaiting description if, having changed the state, you want the original requester to update the description. For example, if the state depends on the information within the response, and you want the requester to classify it — see What state is the request in? above.

Are comments allowed?	The Are comments allowed? setting simply allows you to choose to allow or forbid annotations and comments on this request.
Note that this won’t hide any annotations that have already been left on the reques — it only prevents users adding new ones.

Tags (search keywords)	Enter tags, separated by spaces, that are associated with this request. A tag can be either a simple keyword, or a key-value pair (use a colon as the separator, like this: key:value).
Tags are used for searching. Users and administators both benefit if you tag requests with useful keywords, because it helps them find specific requests — especially if your site gets busy and there are very many in the database.

Although it’s a little more complex than tags on requests, categories also use tags: see more about tags for a little more information.

Resending a request or sending it to a different authority#

If you have corrected the email address for an authority, you can resend an existing request to that authority to the new email address. Alternatively, a user may send a request to the wrong authority. In that situation, you can change the authority on the request and then resend it to the correct authority.

To resend a request, go to the admin interface, click on Requests, then click on the name of the request you want to change. Go to the Outgoing messages heading. Click the chevron next to the first outgoing message, which is the initial request. A panel of information about that message will appear. Click on the Resend button.

To send a request to a different authority, go to the admin interface, click on Requests, then click on the name of the request you want to change. In the Request metadata section, there is a line which shows the authority. Click the move… button next to it. Enter the url_name of the authority that you want to send the request to.

Users, requests and authorities all have url_names. This can be found in the metadata section of their admin page. The url_name makes up the last part of the URL for their public page. So, for a request with the url_name “example_request”, the public page URL will be /request/example_request.
Now click the Move request to authority button. You will see a notice at the top of the page telling you that the request has been moved. You can now resend the request as above.

Hiding a request#

You can hide an entire request. Typically you do this if it’s not a valid Freedom of Information request (for example, a request for personal information), or if it is vexatious.

Go to the admin interface, click on Requests, then click on the title of the request you want. You can hide it in one of two ways:

Hide the request and notify the requester
Hide the request without notifying the requester
Responses to a hidden request will be accepted in the normal way, but because they are added to the request’s page, they too will be hidden.

Hide the request and notify the requester#
Scroll down to the Actions section of the request’s admin page. Choose one of the options next to Hide the request and notify the user:

Not a valid FOI request
A vexatious request
Choosing one of these will reveal an email form. Customise the text of the email that will be sent to the user, letting them know what you’ve done. When you’re ready, click the Hide request button.

Hide the request without notifying the requester#
As well as hiding the request from everyone, you can also use this method if you want to make the request only visible to the requester.
In the Request metadata section of the request’s admin page, click the Edit metadata button. Change the Prominence value to one of these:

requester_only: only the requester can view the request
hidden: nobody can see the request, except administrators.
If you want to hide the request, do not chooose backpage as the prominence. The backpage option stops the request appearing in lists and searches so that it is effectively only visible to anyone who has its URL — but it does not hide the request.
When you’re ready, click the Save changes button at the bottom of the Edit metadata section. No email will be sent to the requester to notify them of what you’ve done.

Deleting a request#

You can delete a request entirely. Typically, you only need to do this if someone has posted private information. If you delete a request, any responses that it has already received will be destroyed as well.

Deleting a request destroys it. There is no “undo” operation. If you're not sure you want to do this, perhaps you should hide the request instead.
Go to the admin interface, click on Requests, then click on the title of the request you want to delete. Click the Edit metadata button. Click on the red Destroy request entirely button at the bottom of the page.

Responses to a deleted request will be sent to the holding pen.
