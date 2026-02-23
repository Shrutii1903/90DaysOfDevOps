# 1. Create an empty file
touch notes.txt

# 2. Write first line
echo "Line 1: Hello EC2 world" > notes.txt

# 3. Append second line
echo "Line 2: Practicing Linux file I/O" >> notes.txt

# 4. Append third line and display using tee
echo "Line 3: This line uses tee" | tee -a notes.txt

# 5. Read the full file
cat notes.txt

# 6. Read first 2 lines
head -n 2 notes.txt

# 7. Read last 2 lines
tail -n 2 notes.txt

What i learned :> writes a line and overwrites the file.

>> appends a line to the file.

tee -a appends and prints to terminal at the same time.

cat reads the full file.

head and tail read specific parts of the file.
