# Publication automatique @chlomo_assouline

Chaque passage (tâche automatique) :
1. Lire posts.json (ce dépôt, branche main).
2. Heure actuelle en Asia/Jerusalem. Publications dues = date == aujourd'hui ET heure prévue <= maintenant < heure prévue + 50 min ET id absent de published.json.
3. Pour chaque publication due, compte Composio `instagram_caper-freon` UNIQUEMENT (ig_user_id 27840624058893162). Vérifier avant tout que le username est bien `chlomo_assouline`, sinon ne rien publier.
4. Anti-doublon : STORY → INSTAGRAM_GET_IG_USER_STORIES, aucune story publiée dans les 40 dernières minutes par cette tâche ; REELS/CAROUSEL → INSTAGRAM_GET_IG_USER_MEDIA, aucune publication de même type dans les 40 dernières minutes.
5. URL des fichiers : https://raw.githubusercontent.com/chlomo111-bit/chlomo-photo-ig/main/<chemin>
   - STORY : INSTAGRAM_POST_IG_USER_MEDIA media_type STORIES, image_url.
   - CAROUSEL : INSTAGRAM_CREATE_CAROUSEL_CONTAINER child_image_urls (ordre), caption exacte.
   - REELS : INSTAGRAM_POST_IG_USER_MEDIA media_type REELS, video_url, cover_url, caption exacte, share_to_feed true.
   - Puis INSTAGRAM_POST_IG_USER_MEDIA_PUBLISH (max_wait_seconds 240 pour un reel), une seule fois.
6. Ajouter l'id dans published.json (avec l'id média et l'heure), commit + push.
7. Rien le samedi (Shabbat). Aucun message à Shlomo sauf problème.
