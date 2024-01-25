# Database Migration Structures

## Summary

This document will discuss things about database standard

## Database

N/A

## Migrations

N/A

## Naming

As discussed on the [page naming conventions](https://www.notion.so/Naming-Conventions-aba0a58d2bec4601a3096f9838d8a087), naming migration is as follows.

**2017\_01\_01\_000000\_verb\_subject\_table**

**can be seen above the naming file migration structure is divided into 2 parts, namely**

* Verb, ex: create
* Subject, ex: articles

There are also 3 types of Migration File Naming, namely

* Initial Migration, ex: **2017\_01\_01\_000000\_create\_articles\_table**

Verb: create

Subject: articles

* Editing Migration, ex: **2017\_01\_01\_000000\_add\_like\_field\_to\_articles\_table**

Verb: add\_like\_field\_to

Subject: articles

* Pivot Migration, ex: **2017\_01\_01\_000000\_create\_user\_role\_table**

Verb: create

Subject: user, and role

#### Table

The table name must be _snake\_case_, ex: user\_profiles, and also use a structure like the following

* Identifiers, ex: id
* Foreign keys, ex: user\_id
* Text Content, ex: blog\_body
* Castable Properties, ex: price
* Timestamps, ex: updated\_at

examples:

```php
public function up(): void
{
    Schema::create('tasks', static function (Blueprint $table): void {
	// Identifiers
        $table->id();
        
        // Foreign Keys
        $table
	    ->foreignId('user_id')
	    ->index()
	    ->constrained()
	    ->cascadeOnDelete();
        
	// Content text
        $table->string('name');
        $table->text('description')->nullable();
        
        // Castable properties
        $table->string('status'); 

	// Timestamps
        $table->dateTime('due_at')->nullable();
        $table->dateTime('completed_at')->nullable();
        $table->timestamps();
    });

}
```
