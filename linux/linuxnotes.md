# Linux alapok

## A Linux könytárszerkezete:
/bin: felhasználó által indítható alap és telepített programok
/boot: grub2 és a kernel fájljait tartalmazza
/dev: eszközök eszközfájljai, indításkor generálódnak kikapcsolás után üres
/etc: konfigurációs fájlok
/lib: közös fájlok mint windowsban a dll fájlok
/mnt: ideiglenesen csatolt eszközökhöz kell például pendrive
/media: mint az /mnt pl, CD/ISO csatoláshoz
/opt: néhány program ide települ - főleg forrásból telepített
/proc: kernelváltozókat tartalmazza futásidőben
/root: rendszergazda könytára
/run: futó folyamatok adatait tartalmazza futásidőben
/srv: szerverfolyamatok megosztásait szokás ide rakni
/sys: eszközök adatait tartalmazza futásidőben
/usr: dokumentációk és egyéb architektúra független adatok tára
/var: logok és ideiglenes tárolás, sok írás történik ide
Könyvtár műveletek
pwd - print working directory
cd - change directory
cd / - root könytárba lépés
cd - home könyvtárba lépés
cd ~ - szintén
cd .. egy szinttel feljebb lépés
Útvonalak elérése: - relatív - a kiindulási ponttól számítva - abszolút - / (root) kiindulási ponttól számítva

man - manual, segítség a parancsok használtában és paraméter listájában

ls - adott könyvtár tartalmának listázása
- -l listázva mutatja
- -a mindent mutat rejtett fájlokat is
- -h human readable

mkdir - mappa létrehozás

rm - törlés - -rf - recursive, force

cp - copy
mv - move; áthelyezés / átnevezés

File műveletek
touch file - üres file létrehozása
nano file - egyszerű fileszerkesztő
find - keresés
- /somewhere - keresés gyökerét meg kell adjuk 1. paraméterként
- -type f / d (file / directory)
- -name névre keresés, akár joker karakterek segítségével

Szöveg műveletek
echo - standard kimenetre ír ki egy karakterláncot
cat - szöveges tartalom kiíratása
more - egy szöveges tartalmat oldalra bontva tördelve jelenít meg, space-el lapozhatunk, q-val léphetünk ki
grep - kereshetünk szövegben
head - egy szöveges tartalom első x sorát jeleníti meg
tail - egy szöveges tartalom utolsó x sorát jeleníti meg; -f paraméterrel nyitva hagyja a file-t és a változó tartalmú file-okat figyelhetjük vele (pl naplófájlok)
cut - egy sornyi szöveget feldarabolhatunk vele és a meghatározott részét fel tudjuk használni;
- -f - a feldarabolt tömb hanyadik elemére vagyunk kíváncsiak
- -d " " - delimiter karakter, ezen mentén fogjuk a darabolást elvégezni

pipeolás ( | ): átirányítja egy parancs eredményét egy következő parancsnak

> egy parancs eredményét fájlba írja ha a fájl már létezett akkor felülírja
>> egy parancs eredményét hozzáfűzi a fájl korábbi tartalmához

User / group műveletek
adduser
addgroup
/etc/passwd
/etc/groups
/etc/shadow

Fájlok, mappák jogosultságainak módosítása
chmod; jogosultságot lehet adni számkóddal vagy karakteresen
jogosultságot lehet adni számkóddal vagy karakteresen
számkoddal:
- 4 olvasási jog r
- 2 írási jog w
- 1 futtatási jog x
a számok összegét kell megadni jogosultsági csoportonként:
pl.: chmod -R 764 testdirectory
a fájl tulajdonosa mindent csinálhat 4+2+1=7
a csoport írhatja és olvashatja 4+2=6
mindenki más csak olvashatja a testlabdirectory-t és a benne lévő összes fájlt és mappát

karakteresen:
- u user
- g group
- o other
a célcsoport összevonható egy parancsba például 'go' (group és other)
jogosultság adása + jellel
elvétele - jellel
chmod g+rx fájlnév - írási és futtatási jogot ad a filenak chmod go-r fájlnév elveszi az olvasási jogot a csoporttól és a többi felhasználótól
