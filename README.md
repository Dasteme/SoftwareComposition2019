# SoftwareComposition2019
Analysing cryptographic questions on online sources

Data can be downloaded from [Data.StackExchange](https://data.stackexchange.com/stackoverflow/query/new)

Used query to download posts with the tag `cryptography` as CSV file:

```sql
SELECT questions.Id as [post_link], questions.title as [title], questions.body as [body_question],
answers.body as [body_answer],
answers.id as [answer_id],
questions.viewcount as [viewcount],
questions.Tags as [tags],
questions.Score as [score],
answers.Score as [score_answer],
questions.AnswerCount as [answercount],
questions.LastActivityDate,
questions.AcceptedAnswerId,
questions.CommentCount,
questions.FavoriteCount,
questions.LastEditorUserId,
questions.LastEditorDisplayName,
questions.LastEditDate,
questions.CreationDate,
questions.ClosedDate,
answers.LastEditDate as [answer_LastEditDate],
answers.CreationDate as [answer_CreationDate]
FROM Posts questions
left JOIN Posts answers ON answers.parentid = questions.id
WHERE questions.Tags like '%<cryptography>%'
order by questions.viewcount DESC
```
