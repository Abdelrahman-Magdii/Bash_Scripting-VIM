### ✍️ Writing (saving) in Vim

1. **Open a file** in Vim:

   ```bash
   vim filename.txt
   ```

2. **Enter insert mode** (to start typing text):

   * Press `i` → insert before cursor
   * Press `a` → append after cursor
   * Press `o` → open new line below
     *(you’ll see `-- INSERT --` at the bottom)*

3. **Type your text** as normal.

4. **Save your work (write to file):**

   * Press `Esc` (to leave insert mode and go back to command mode).
   * Then type:

     * `:w` → save (write) the file.
     * `:wq` → save **and quit**.
     * `:x` → same as `:wq`.
     * `:q!` → quit **without saving**.

---

### 🚀 Quick shortcuts

* `ZZ` (Shift + ZZ) → save and quit.
* `ZQ` (Shift + ZQ) → quit without saving.

---

✅ Example workflow:

1. `vim notes.txt`
2. Press `i`, write: *Hello Vim!*
3. Press `Esc` → type `:wq` → Enter.

Now `notes.txt` is saved.

