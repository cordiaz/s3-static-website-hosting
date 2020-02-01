## Membuat static Web menggunakan AWS S3

### Setting S3
- membeli sebuah domain, misalnya: awanera.com
- membuat sub-domain: service.awanera.com
- create bucket s3 sesuai FQDN: service.awanera.com
	- region: Asia Pasicif (Singapore)
- membuat 2 file di local Anda: (1) index.html dan (2) error.html
- upload file index.html dan error.html ke bucket service.awanera.com
- klik tab properties pilih static web hosting
	- pilih use this bucket to host a website
	- isi index document dengan index.html dan error document dengan error.html
	- catat endpoint-nya: http://service.awanera.com.s3-website-ap-southeast-1.amazonaws.com
	- klik save
- klik tab permission, pada tombol Edit, un-checklist block all public access, klik save
	- ketik confirm pada kolom yang tersedia, klik confirm
- klik tab overview
	- klik index.html, klik tombol make public. klik object url, akan tampil content dari file index.html
	- lakukan hal yang sama untuk file error.html

### Setting Route53
- create hosted zones awanera.com
	- domain name: awanera.com
	- comment: bebas
	- type: public hosted zones
- create record set service.awanera.com
	- isi name dengan service
	- pilih alias Yes
	- alias target: s3-website-ap-southeast-1.amazonaws.com (endpoint s3), klik create

### Uji
- pilih record name set: service.awanera.com
- klik test record set
- klik get response, perhatikan bagian DNS response code: NOERROR. Artinya setting DNS sudah berhasil.
- selesai
