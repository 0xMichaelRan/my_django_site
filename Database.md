Here is the shell command for database (sqlite3)
https://docs.djangoproject.com/en/1.10/intro/tutorial02/

    from polls.models import Question, Choice   # Import the model classes we just wrote.
    Question.objects.all()
    from django.utils import timezone
    q = Question(question_text="What's new?", pub_date=timezone.now())
    q.save()
    q.id
    q.question_text
    q.pub_date
    q.question_text = "What's up?"
    q.save()
    Question.objects.all()

