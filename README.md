# Patika SQL Bootcamp — Ödev 12

Patika.dev SQL bootcamp'inin **12. ödevi**. Alt sorgular (subqueries) ve `JOIN` + `GROUP BY` ile veri analizi.

**Örnek veritabanı:** DVD Rental (Pagila) — `film`, `payment`, `customer` tabloları.

## 📌 Kapsanan Konular

- Skaler alt sorgu: `WHERE ... = (SELECT ...)`
- Alt sorgu içinde `AVG`, `MAX`, `MIN`
- `JOIN` + `GROUP BY` + `ORDER BY` + `LIMIT`
- Takma ad (`AS`)

## 📝 Sorgular

```sql
-- 1. Ortalamadan uzun film sayısı
SELECT COUNT(*) FROM film
WHERE length > (SELECT AVG(length) FROM film);

-- 2. En yüksek rental_rate'e sahip film sayısı
SELECT COUNT(*) FROM film
WHERE rental_rate = (SELECT MAX(rental_rate) FROM film);

-- 3. En düşük rental_rate ve replacement_cost'a sahip filmler
SELECT title, rental_rate, replacement_cost FROM film
WHERE rental_rate = (SELECT MIN(rental_rate) FROM film)
  AND replacement_cost = (SELECT MIN(replacement_cost) FROM film);

-- 4. En çok alışveriş yapan 10 müşteri
SELECT customer.first_name, customer.last_name, COUNT(*) AS total_payments
FROM payment
JOIN customer ON payment.customer_id = customer.customer_id
GROUP BY payment.customer_id
ORDER BY total_payments DESC
LIMIT 10;
```

## 👤 Yazar

**Sena Saygın Şenyüz** — Endüstri Mühendisi & Veri Analisti | ECBA® Sertifikalı
