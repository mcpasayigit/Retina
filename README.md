# retina-gm-statik

retina-gm.com sitesinin statik kopyası (HTML, CSS, JS, görseller, dokümanlar).

- `site/`: sitenin kopyası. Dosyalar sunucudan geldiği gibi, bayt bayt aynı kaydedilir. PHP ve WordPress paneli yoktur.
- `report/rapor.md`: son indirmenin raporu (eksikler, dış kaynaklar, şüpheli kod belirtileri).
- `report/manifest.json`: her dosyanın boyutu ve SHA-256 değeri.
- `scripts/mirror.py`: indirme scripti (Python, ek paket gerektirmez).
- `.github/workflows/mirror.yml`: Actions sekmesinde **Siteyi kopyala** → **Run workflow** ile yeniden indirir.

## Veridyen / cPanel'e kurulum

- `.cpanel.yml`: cPanel > Git Version Control > **Deploy HEAD Commit** ile `site/` klasörünü `/home/retinagm/public_html/` altına kopyalar. cPanel kullanıcı adı `retinagm` değilse `DEPLOYPATH` satırını değiştir.
- `deploy/htaccess`: `public_html/.htaccess` olarak kopyalanır. `www` adresini `retina-gm.com`a, `http` adresini `https`e yönlendirir ve 404 sayfasını ayarlar.
- `main` dalına zorla gönderim (force push) yapma: cPanel "Update from Remote" yalnızca ileri sarmayı (fast-forward) kabul eder.

Bu repo özel (private) kalmalı. Site olduğu gibi kopyalandığı için içindeki olası zararlı kodlar da kopyalanmıştır;
temizlenmeden yayınlanmamalıdır (rapordaki "Dikkat" bölümüne bakın).
