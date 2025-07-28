# Octra Testnet Rehberi

**Octra testnet** sürecinde yapılması gereken tüm adımları en anlaşılır haliyle bulabilirsiniz. Rehber zamanla güncellenecektir

---

## Ön Hazırlık

Testnet'e katılmak için bir **Octra cüzdanı** oluşturmanız gerekiyor.  
Cüzdan oluşturma adımlarını [burada](https://t.me/GoldenZoneWeb3/11466) anlattık:

---

## Sunucuyu Güncelleyelim

```bash
sudo apt update -y && sudo apt upgrade -y
```
---

## Python Kurulu Değilse Yükleyelim

```bash
sudo apt install python3 python3-venv python3-pip -y
```
---

## Octra Klasörü Oluşturun

```bash
mkdir octra
cd octra
```
---

## Preclient Yükleme ve Çalıştırma

```bash
git clone https://github.com/octra-labs/octra_pre_client.git
cd octra_pre_client
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
cp wallet.json.example wallet.json
```
---

## Cüzdan Bilgilerini Düzenleme

```bash
nano wallet.json
```
- Aşağıdaki şekilde düzenledikten sonra kaydetmek için CTRL'ye basılı tutup X + Y ardından Enter basalım.

```bash
{
  "priv": "B64 priv key buraya",
  "addr": "adres buraya",
  "rpc": "https://octra.network"
}
```
---

## Preclient'i Çalıştırın

```bash
./run.sh
```
- Terminalde çıkan adımları sırasıyla uygulayın. Birbirinize token göndererek işlem yapabilirsiniz. Kurcalayın. Her şeyi yapınca devam edin.

---

## Rust Kuralım

```bash
cd
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env
```
---

## Diğer Kısıma Geçelim

```bash
cd octra
git clone https://github.com/octra-labs/ocs01-test.git
cd ocs01-test
cargo build --release
cp EI/exec_interface.json .
```
---

## Tekrar Cüzdan Import Ediyoruz

```bash
nano wallet.json
```
- Aşağıdaki şekilde düzenledikten sonra kaydetmek için CTRL'ye basılı tutup X + Y ardından Enter basalım.

```bash
{
  "priv": "B64 priv key buraya",
  "addr": "adres buraya",
  "rpc": "https://octra.network"
}
```
---

## Testi Başlatıyoruz

```bash
./target/release/ocs01-test
```

- Terminalde çıkan görevleri sırayla tamamlamaya çalışın.
- Claim adımını yapamıyorsanız, daha önce bir TX yapmadığınız içindir. Başkalarına Oct göndererek bu sorunu çözebilirsiniz.
