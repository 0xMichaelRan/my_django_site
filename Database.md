Here is the shell command for database (sqlite3)
https://docs.djangoproject.com/en/1.10/intro/tutorial02/

    python3 manage.py shell

After you saw ">>>", try out the following:

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
    quit()

After adding __str__(self) function: 

    from polls.models import Question, Choice
    Question.objects.all()
    Question.objects.filter(id=1)
    Question.objects.filter(question_text__startswith='What')
    from django.utils import timezone
    current_year = timezone.now().year
    Question.objects.get(pub_date__year=current_year)
    Question.objects.get(id=2)
    Question.objects.get(pk=1)
    q = Question.objects.get(pk=1)
    q.was_published_recently()

Now add some choices to the question:

    q = Question.objects.get(pk=1)
    q.choice_set.all()
    q.choice_set.create(choice_text='Not much', votes=0)
    q.choice_set.create(choice_text='The sky', votes=0)
    c = q.choice_set.create(choice_text='Just hacking again', votes=0)
    c.question
    q.choice_set.all()
    q.choice_set.count()

Use double underscores to separate relationships (automatically follows). 

    Choice.objects.filter(question__pub_date__year=current_year)
    c = q.choice_set.filter(choice_text__startswith='Just hacking')
    c.delete()
    quit()

