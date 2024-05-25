# We will use the python interpreter (Python shell) to add some members to it.
    py manage.py shell
# After the three >>> write following:
    >>> from members.models import Member
    >>> Member.objects.all()
# This should give you empty QuerySet object, just like
    <QuerySet []>
# Add a record to the table, by executing these two lines.
    >>> member = Member(firstname='Emil', lastname='Refsnes')
    >>> member.save()
# Execute this command to see if the Member table got a member.
    >>> Member.objects.all().values()
# Hopefully, the result will look like this:
    <QuerySet [{'id':1, 'firstname': 'Emil', 'lastname': 'Refsnes'}]>


## Add Multiple Records
# You can add multiple records by making a list of Member objects, and execute .save() on each entry:
    >>> member1 = Member(firstname="Tobias", lastname="Refsnes")
    >>> member2 = Member(firstname="Linus", lastname="Refsnes")
    >>> member3 = Member(firstname="Lene", lastname="Refsnes")
    >>> member4 = Member(firstname="Stale", lastname="Refsnes")
    >>> member5 = Member(firstname="Jane", lastname="Refsnes")
    >>> member_list = [member1, member2, member3, member4, member5]
    >>> for x in member_list:
    >>>     x.save()
# Now there are 6 members in the Member table:
    >>> Member.objects.all().values()
    <QuerySet [{'id': 1, 'firstname': 'Emil', 'lastname': 'Refsnes'}, 
    {'id': 2, 'firstname': 'Tobias', 'lastname': 'Refsnes'}, 
    {'id': 3, 'firstname': 'Linus', 'lastname': 'Refsnes'}, 
    {'id': 4, 'firstname': 'Lene', 'lastname': 'Refsnes'}, 
    {'id': 5, 'firstname': 'Stale', 'lastname': 'Refsnes'}, 
    {'id': 6, 'firstname': 'Jane', 'lastname': 'Refsnes'}]>