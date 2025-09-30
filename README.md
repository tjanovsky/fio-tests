# fio-tests
Collection of practical fio tests

## Installation

**Ubuntu/Debian:**
```bash
apt install fio
```

**RHEL/CentOS/Fedora:**
```bash
dnf install fio
```

**macOS:**
```bash
brew install fio
```

**From source:**
```bash
git clone https://github.com/axboe/fio.git
cd fio
./configure
make
make install
```

## Usage

**Basic run:**
```bash
fio jobfile.fio
```

**Save output to file:**
```bash
fio jobfile.fio --output=results.txt
```

**JSON output for parsing:**
```bash
fio jobfile.fio --output-format=json --output=results.json
```

**Run specific job from file:**
```bash
fio jobfile.fio --section=rand-read-4k
```

**Override parameters:**
```bash
fio jobfile.fio --runtime=300 --size=10G
```

**Quick one-liner test:**
```bash
fio --name=test --rw=randread --bs=4k --size=1G --runtime=60 --time_based
```

**Test on specific directory:**

*WARNING!* Do not use block device as the target, or it wipes out the whole disk!

```bash
fio jobfile.fio --directory=/mnt/test
```

**Multiple output formats:**
```bash
fio jobfile.fio --output=results.txt --output-format=normal --write_lat_log=latency
```

## Environment Variables

Job files support environment variable substitution:
```bash
TEST_DIR=/mnt/nvme SIZE=10G RUNTIME=300 fio jobfile.fio
```
