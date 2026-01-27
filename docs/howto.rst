***********************
How to Tag IATI Data
***********************

There are two primary methods to link an IATI activity to a GFNS Preparedness Plan:

* **Method A**: Using the IATI “Tag” Data Field (Preferred)
* **Method B**: Supplementing with Free Text Hashtags

Method A: Using the IATI "Tag" Data Field (Preferred)
=======================================================

The `IATI tag element <https://iatistandard.org/en/iati-standard/203/activity-standard/iati-activities/iati-activity/tag/>`_ allows for the inclusion of non-statistical classifications within an activity.

+--------------------------------------------------------------------------------------------+----------------------------------+--------------+-----------------------------------------------------------------------------------------------------------------+
| Data Field                                                                                 | Purpose                          | Requirement? | GFNS Value                                                                                                      |
+============================================================================================+==================================+==============+=================================================================================================================+
| `Tag Vocabulary <https://iatistandard.org/en/iati-standard/203/codelists/tagvocabulary/>`_ | Identifies the GFNS list         | Required     | 5                                                                                                               |
+--------------------------------------------------------------------------------------------+----------------------------------+--------------+-----------------------------------------------------------------------------------------------------------------+
| Tag Code                                                                                   | Country of the Preparedness Plan | Required     | `Two-digit ISO code <https://iatistandard.org/en/iati-standard/203/codelists/country/>`_ (e.g., SO for Somalia) |
+--------------------------------------------------------------------------------------------+----------------------------------+--------------+-----------------------------------------------------------------------------------------------------------------+
| Tag Narrative                                                                              | Descriptive title of the plan    | Optional     | e.g., "Somalia Preparedness Plan..."                                                                            |
+--------------------------------------------------------------------------------------------+----------------------------------+--------------+-----------------------------------------------------------------------------------------------------------------+

| 

Technical Implementation (XML):
---------------------------------

In the IATI XML, the code and vocabulary attributes must be present.

Standard usage: 

.. code-block:: XML

    <tag vocabulary="5" code="SO"/>


With optional narrative: 

.. code-block:: XML

    <tag vocabulary="5" code="SO" >
        <narrative>Somalia Preparedness Plan for Food and Nutrition Security Crises</narrative>
    </tag>

Method B: Supplementing with Free Text & Hashtags
=======================================================

If your system cannot support the tag field, or if you want to provide more context, use hashtags in free-text fields like the activity 
`title <https://iatistandard.org/en/iati-standard/203/activity-standard/iati-activities/iati-activity/title/>`_ , 
`description <https://iatistandard.org/en/iati-standard/203/activity-standard/iati-activities/iati-activity/description/>`_, 
and/or `transaction description <https://iatistandard.org/en/iati-standard/203/activity-standard/iati-activities/iati-activity/transaction/description/>`_ .

To make these hashtags relevant to GFNS, a specific string is required (see :ref:`country_tags` for full list) that combines #GFNS with the ISO country code.  
For example, #GFNS-YE to related to the Preparedness Plan in Yemen.

+---------------------------+------------------+---------------------------------------------------------------+
| Preparedness Plan Country | Required Hashtag | Example of Usage                                              |
+===========================+==================+===============================================================+
| Somalia                   | #GFNS-SO         | Activity title: "Food Security programme in Somalia #GFNS-SO" |
+---------------------------+------------------+---------------------------------------------------------------+
| Haiti                     | #GFNS-HT         | Activity description: "This activity relates to #GFNS-HT"     |
+---------------------------+------------------+---------------------------------------------------------------+
| Yemen                     | #GFNS-YE         | Transaction description: "Commitment towards #GFNS-YE"        |
+---------------------------+------------------+---------------------------------------------------------------+

| 

Technical Implementation (XML):
---------------------------------

In the IATI XML, this hashtag will be included in the narrative sub-element for any of title, description, or transaction description.

Example usage - activity description:

.. code-block:: XML

    <description type="1" >
        <narrative>This project is in response to food insecurity in Haiti, and is a response to emerging needs. This activity relates to #GFNS-HT</narrative>
    </description>

