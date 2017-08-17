The value that indicates whether the element was added, updated, or deleted. For possible values, see [ChangeTypeReportFilter](http://msdn.microsoft.com/library/8f975b9c-f939-45bc-9494-234ad3d56f34).

For adds, the *NewValue* column contains the added entity. For deletes, the *OldValue* column contains the deleted entity. For updates, the *NewValue* column contains the new value and the *OldValue* column contains the old value.

If an entity which has a delivery status property was added, for example a campaign, the value of *HowChanged* is Added. To report a deleted entity,  the *ItemChanged* field is Status, the *HowChanged* field is Changed, and the *NewValue* field is Deleted.

Associating a target with a campaign or ad group will be reported as an add change. The *AttributeChanged* column will identify the target types contained in the target object. Updates to a target object will be reported as a delete change and an add change. Removing a campaign's or ad group's association with a target object will be reported as a delete change.

