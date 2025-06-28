# 📝 Guida: Ripristinare il Menu Contestuale Classico (Windows 10) su Windows 11

## ✅ Obiettivo

Visualizzare **sempre il menu contestuale classico** (quello completo con "Apri con", "Invia a", ecc.) quando fai clic col tasto destro su file o cartelle in **Windows 11**, senza dover cliccare ogni volta su **"Mostra altre opzioni"**.

---

## 🛠️ Cosa abbiamo fatto?

Abbiamo aggiunto una **chiave nel Registro di sistema (regedit)** per disattivare il nuovo menu di Windows 11 e forzare il sistema a mostrare **direttamente il menu classico** (quello usato in Windows 10).

Questa modifica sfrutta una “scorciatoia” riconosciuta da Windows per **svuotare il handler predefinito del menu contestuale**.

---

## 🧪 Procedura Dettagliata

### 1. Apri il registro di sistema

* Premi `Win + R`
* Scrivi `regedit` → premi **Invio**

### 2. Vai a questa chiave

```text
HKEY_CURRENT_USER\Software\Classes\CLSID
```

### 3. Crea una nuova chiave

* Clic destro su `CLSID` → **Nuovo > Chiave**
* Nominala esattamente così:

```text
{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}
```

### 4. Crea una sotto-chiave

* Clic destro su questa nuova chiave → **Nuovo > Chiave**
* Nominala:

```text
InprocServer32
```

### 5. Imposta il valore predefinito vuoto

* Seleziona `InprocServer32`
* A destra, fai doppio clic su **(Predefinito)**
* **Non scrivere nulla**, lascia il campo vuoto → clicca **OK**

### 6. Riavvia il computer

Oppure, per applicare subito:

* Premi `Ctrl + Shift + Esc` per aprire il **Task Manager**
* Trova **Esplora risorse (Windows Explorer)** → clic destro → **Riavvia**

---

## ✅ Risultato

Ora ogni clic destro aprirà **direttamente il menu classico**, senza passare per “Mostra altre opzioni”.

---

## 🔄 Come tornare indietro (ripristinare menu moderno)

1. Apri di nuovo `regedit`
2. Vai a:

    ```text
    HKEY_CURRENT_USER\Software\Classes\CLSID
    ```

3. Elimina la chiave:

    ```text
    {86ca1aa0-34aa-4e8b-a509-50c905bae2a2}
    ```

4. Riavvia il computer o Esplora risorse
