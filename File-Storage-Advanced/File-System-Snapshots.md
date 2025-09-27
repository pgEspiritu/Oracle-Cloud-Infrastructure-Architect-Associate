# Lesson: File System Snapshots

## What Are Snapshots?
- Snapshots provide **data protection** for your file systems.  
- They are a **consistent, point-in-time view** of your file system.  
- Snapshots are accessible under the root directory of the file system at:  
```text
.snapshot/<snapshot_name>
```

---

## Example
- A snapshot created in the **OCI Console** with the name `22AprilSnapshot`  
- When accessing the mounted file system on an instance, the snapshot is available under:  
```text
/.snapshot/22AprilSnapshot
```

---

## Storage Usage of Snapshots
- Snapshots **initially consume no additional storage**.  
- This is because they **reference the original data** rather than duplicating it.  

### Benefits:
- **Cost Efficiency** → Since they don’t duplicate data, initial usage cost is limited.  
- **Metered on Changes** → Storage usage is only measured against data that has changed since the last snapshot.  
- If nothing has changed in the file system, **new snapshots do not consume extra storage**.

---

## Summary
In this lesson, we discussed:  
- The purpose of **file system snapshots**  
- How they provide a **point-in-time view** of data  
- Their **cost efficiency** through space-saving mechanisms  
