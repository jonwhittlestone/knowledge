# Python/Django Language Hints from diffs

List Comprehensions.
GL Diff: https://goo.gl/QLynPz
----
Django Querysets - just ids
    
    return EntityField.objects.filter(
        source_format_id=self.sourceformat_id
        ).values_list('id', flat=True)
        
----
Django Lookups that span relationships
GL Diff: https://goo.gl/37mP1d
Django Docs :https://docs.djangoproject.com/en/1.11/topics/db/queries/#lookups-that-span-relationship://docs.djangoproject.com/en/1.11/topics/db/queries/#lookups-that-span-relationships  
----

