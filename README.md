# ORM Framework Spec
My ORM framework specificaton taking the best ideas from the major framework out there.

## Creating and configuring a Model
### Annotation

#### Java Persistence Architecture
In Java EE/Jakarta EE with JPA, the main annotations to define an entity are:

* @Entity – Marks a class as a JPA entity.
* @Table – Specifies the database table name.
* @Id – Marks the primary key field.
* @GeneratedValue – Specifies primary key generation strategy.
* @Column – Customizes column mapping.
* @Transient – Excludes a field from persistence.
* @Lob – Marks a field as a Large Object (BLOB or CLOB).
* @Enumerated – Specifies how enums should be stored.
* @Temporal – Defines date/time mapping (DATE, TIME, TIMESTAMP).
* @Version – Marks a field for optimistic locking.
* @Embedded – Embeds another object in the entity.
* @Embeddable – Marks a class as embeddable.
* @AttributeOverride – Overrides mapping in an embedded entity.
* @AttributeOverrides – Defines multiple attribute overrides.
* @Access – Defines property vs. field-based access.

For relationships: 
* @OneToOne – Defines a one-to-one relationship.
* @OneToMany – Defines a one-to-many relationship.
* @ManyToOne – Defines a many-to-one relationship.
* @ManyToMany – Defines a many-to-many relationship.
* @JoinColumn – Specifies a foreign key column.
* @JoinTable – Defines a join table for @ManyToMany.
* @MappedSuperclass – Specifies a base class without its own table.
* @Inheritance – Defines inheritance strategy.
* @DiscriminatorColumn – Defines the column to store entity type in SINGLE_TABLE inheritance.
* @DiscriminatorValue – Specifies the entity type value.

#### Entity Framework Core
**Table**
* [Table("Blogs")]

**Column**
* [Column(Order = 0)]
* [Column("blog_id")]
* [Column(TypeName = "varchar(200)")]
* [Required]
* [MaxLength(500)]
* [Precision(14, 2)]
* [Unicode(false)]
* [Comment("The URL of the blog")]

* [Column("ColumnName")] – Specifies the column name.
* [Key] – Marks the primary key.
* [DatabaseGenerated(DatabaseGeneratedOption.None | Identity | Computed)] – Controls how values are generated.
* [Required] – Marks a column as NOT NULL.
* [MaxLength(n)] / [StringLength(n)] – Sets the maximum length of a string.
* [Timestamp] – Marks a column as a timestamp for concurrency control.
* [ConcurrencyCheck] – Marks a column for concurrency checking.
* [ForeignKey("NavigationPropertyName")] – Defines a foreign key.
* [Index("IndexName", Order = 1, IsUnique = true)] (Only in EF6) – Defines an index.
* [NotMapped] – Excludes a property from the database mapping.
* [InverseProperty("NavigationPropertyName")] – Specifies multiple relationships between the same entities.

#### SQLAlchemy
In SQLAlchemy, the main attributes to define a table within a Declarative model are:

Basic Table Definition
* __tablename__ – Specifies the table name.
* Column – Defines a column in the table.

Column Attributes
* Integer, String, Text, Float, Boolean, DateTime, Date, Time, LargeBinary, Enum, etc. – Define column data types.
* primary_key=True – Marks a column as the primary key.
* autoincrement=True – Enables auto-increment behavior.
* nullable=False – Prevents NULL values.
* unique=True – Enforces a unique constraint.
* index=True – Creates an index on the column.
* default=<value> – Sets a default value.
* server_default=<value> – Defines a default at the database level.
* ForeignKey('<table>.<column>') – Defines a foreign key relationship.

Relationships & Foreign Keys
* relationship('<Model>') – Defines an ORM relationship.
* backref='<attribute>' – Adds a reverse relation.
* back_populates='<attribute>' – Explicitly sets the related attribute.
* cascade="<cascade_options>" – Defines cascade delete/update behavior.
* lazy="<loading_strategy>" – Controls how relationships are loaded.

Composite & Hybrid Properties
* @hybrid_property – Defines computed properties.
* @hybrid_method – Defines computed methods in queries.
* @declared_attr – Customizes class attributes dynamically.

Table Constraints & Indexes
* UniqueConstraint – Defines a table-level uniqueness constraint.
* CheckConstraint – Enforces custom constraints.

Index – Defines indexes.
Table-Level Attributes
* __table_args__ – Defines constraints, indexes, and other table-level arguments.

This covers the core attributes needed to define a table in SQLAlchemy ORM. Let me know if you need further details.

