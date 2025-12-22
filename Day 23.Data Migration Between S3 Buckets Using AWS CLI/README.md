✅ STEP 1 — Create the New S3 Bucket

Run this command in us-east-1:

```
aws s3 mb s3://datacenter-sync-14788 --region us-east-1
```


S3 buckets are private by default — no extra action needed.

✅ STEP 2 — Sync (Copy) All Data From the Source Bucket

Existing bucket (source):

datacenter-s3-12806


New bucket (destination):

datacenter-sync-14788


Run:
```
aws s3 sync s3://datacenter-s3-12806 s3://datacenter-sync-14788
```

This copies:

All objects

All folders

Maintains structure

Skips duplicates on re-run

✅ STEP 3 — Verify the Data Migration
✔ Check number of files and total size

```
# Source:

aws s3 ls s3://datacenter-s3-12806 --recursive --summarize


# Destination:

aws s3 ls s3://datacenter-sync-14788 --recursive --summarize
```

Both should show the same number of files and the same total size.

```
# Dry-run comparison (should show no differences)
aws s3 sync s3://datacenter-s3-12806 s3://datacenter-sync-14788 --dryrun
```

---