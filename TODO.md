# TODO List for SQLAlchemy-Serializer Implementation

## Plan
1. Update Zookeeper model to inherit from SerializerMixin and add serialize_rules
2. Update Enclosure model to inherit from SerializerMixin and add serialize_rules
3. Update Animal model to inherit from SerializerMixin and add serialize_rules
4. Run pytest to verify all tests pass
5. Git add and commit the changes

## Implementation Details

### Changes to server/models.py:

1. **Zookeeper** (line 19):
   - Change: `class Zookeeper(db.Model):` → `class Zookeeper(db.Model, SerializerMixin):`
   - Add after __tablename__: `serialize_rules = ('-animals.zookeeper',)`

2. **Enclosure** (line 34):
   - Change: `class Enclosure(db.Model):` → `class Enclosure(db.Model, SerializerMixin):`
   - Add after __tablename__: `serialize_rules = ('-animals.enclosure',)`

3. **Animal** (line 46):
   - Change: `class Animal(db.Model):` → `class Animal(db.Model, SerializerMixin):`
   - Add after __tablename__: `serialize_rules = ('-zookeeper.animals', '-enclosure.animals',)`

