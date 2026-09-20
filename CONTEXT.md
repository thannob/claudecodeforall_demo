# Thai Food Recommender

A single-page site that suggests a Thai dish to eat today and lets the visitor keep a personal list of favorites.

## Language

**Dish**:
One Thai food item in the fixed catalog of 9, with a name, one-line description, category, and emoji icon.
_Avoid_: Food, item, recipe

**Category**:
The type of dish (e.g. แกง, ผัด, ยำ, ต้ม/ซุป, ของหวาน, เส้น). Used only as a label shown with a Dish, not a filter or navigation concept.

**Today's Pick**:
The single Dish currently shown as the result of the random button. Re-rolling replaces it, skipping the Dish that was just shown so the same Dish never appears twice in a row.
_Avoid_: Result, selection, current dish

**Favorite**:
A Dish the visitor has marked as liked, persisted in `localStorage` by Dish name so it survives reloads. Toggled from either Today's Pick or the Menu; both reflect the same underlying state.
_Avoid_: Like (as a noun), saved item, bookmark

**Menu**:
The full, always-visible list of all 12 Dishes, each with its own like control. Distinct from Today's Pick, which shows only the one Dish the random button most recently selected.
_Avoid_: Catalog, list, all dishes

**Member**:
A visitor who has registered with full name, email, and phone via the signup form. Stored as a row in the `members` table of the `thaifood` Supabase project (not `localStorage`), separate from Favorites. Registration is write-only from the site — no login, session, or member-facing data retrieval exists.
_Avoid_: User, account, subscriber
