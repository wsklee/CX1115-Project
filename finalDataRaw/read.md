JSON_COLUMNS = {
    'genres',
    'keywords',
    'production_countries',
    'production_companies',
    'spoken_languages'
                }

KEYS_TO_DROP = {
    'adult',
    'backdrop_path',
    'belongs_to_collection',
    'imdb_id',
    'poster_path',
    'profile_path',
    'video',
    'homepage',
    'credits'
                }
                
# Drop those with no id
if len(df[df.id.isnull()]) > 0:
print(f'Dropping {len(df[df.id.isnull()])} entries without ids')
df = df[~df.id.isnull()]
# Download English movies only
df = df.loc[(df['original_language']=='en')]
