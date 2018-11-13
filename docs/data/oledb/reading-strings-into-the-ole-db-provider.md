---
title: Lecture de chaînes dans le fournisseur OLE DB
ms.date: 10/13/2018
helpviewer_keywords:
- OLE DB providers, reading strings into
ms.assetid: 517f322c-f37e-4eed-bf5e-dd9a412c2f98
ms.openlocfilehash: 50df9f13b814eb00b309460894d704238bc3e7dc
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51264774"
---
# <a name="reading-strings-into-the-ole-db-provider"></a>Lecture de chaînes dans le fournisseur OLE DB

Le `CCustomRowset::Execute` fonction ouvre un fichier et lit les chaînes. Le consommateur passe le nom de fichier au fournisseur en appelant [ICommandText::SetCommandText](/previous-versions/windows/desktop/ms709757). Le fournisseur reçoit le nom de fichier et le stocke dans la variable membre `m_strCommandText`. `Execute` lit le nom de fichier à partir de `m_strCommandText`. Si le nom de fichier n’est pas valide ou le fichier n’est pas disponible, `Execute` retourne une erreur. Sinon, il ouvre le fichier et appelle `fgets` pour récupérer les chaînes. Pour chaque jeu de chaînes qu’il lit, `Execute` crée une instance de l’enregistrement utilisateur (modifié `CCustomWindowsFile` de [stocker des chaînes dans le fournisseur OLE DB](../../data/oledb/storing-strings-in-the-ole-db-provider.md)) et le place dans un tableau.

Si le fichier ne peut pas être ouvert, `Execute` doit retourner DB_E_NOTABLE. Si elle retourne E_FAIL à la place, le fournisseur ne fonctionnera pas avec beaucoup de consommateurs et ne sont pas transmettre OLE DB [tests de compatibilité](../../data/oledb/testing-your-provider.md).

## <a name="example"></a>Exemple

```cpp
/////////////////////////////////////////////////////////////////////////
// CustomRS.h
class CCustomRowset : public CRowsetImpl< CCustomRowset, CCustomWindowsFile, CCustomCommand>
{
public:
    HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)
    {
        enum {
            sizeOfBuffer = 256,
            sizeOfFile = MAX_PATH
        };
        USES_CONVERSION;
        FILE* pFile = NULL;
        TCHAR szString[sizeOfBuffer];
        TCHAR szFile[sizeOfFile];
        size_t nLength;

        ObjectLock lock(this);

        // From a filename, passed in as a command text, scan the file
        // placing data in the data array.
        if (!m_strCommandText)
        {
            ATLTRACE("No filename specified");
            return E_FAIL;
        }

        // Open the file
        _tcscpy_s(szFile, sizeOfFile, m_strCommandText);
        if (szFile[0] == _T('\0') ||
            (fopen_s(&pFile, (char*)&szFile[0], "r") == 0))
        {
            ATLTRACE("Could not open file");
            return DB_E_NOTABLE;
        }

        // Scan and parse the file.
        // The file should contain two strings per record
        LONG cFiles = 0;
        while (fgets((char*)szString, sizeOfBuffer, pFile) != NULL)
        {
            nLength = strnlen((char*)szString, sizeOfBuffer);
            szString[nLength-1] = '\0';   // Strip off trailing CR/LF
            CCustomWindowsFile am;
            _tcscpy_s(am.szCommand, am.iSize, szString);
            _tcscpy_s(am.szCommand2, am.iSize, szString);

            if (fgets((char*)szString, sizeOfBuffer, pFile) != NULL)
            {
                nLength = strnlen((char*)szString, sizeOfBuffer);
                szString[nLength-1] = '\0'; // Strip off trailing CR/LF
                _tcscpy_s(am.szText, am.iSize, szString);
                _tcscpy_s(am.szText2, am.iSize, szString);
            }

            am.dwBookmark = ++cFiles;
            if (!m_rgRowData.Add(am))
            {
                ATLTRACE("Couldn't add data to array");
                fclose(pFile);
                return E_FAIL;
            }
        }

        if (pcRowsAffected != NULL)
            *pcRowsAffected = cFiles;
        return S_OK;
    }
};
```

Dans ce cas, votre fournisseur doit être prêt à compiler et exécuter. Pour tester le fournisseur, vous avez besoin d’un consommateur avec la fonctionnalité de correspondance. [Implémentation d’un consommateur Simple](../../data/oledb/implementing-a-simple-consumer.md) montre comment créer un tel un consommateur de test. Exécutez le consommateur de test avec le fournisseur et vérifiez que le consommateur de test récupère les chaînes appropriées à partir du fournisseur.

Lorsque vous avez testé avec succès votre fournisseur, vous souhaiterez peut-être améliorer son fonctionnement en implémentant des interfaces supplémentaires. Voici un exemple dans [amélioration le fournisseur Simple accessible en lecture seule](../../data/oledb/enhancing-the-simple-read-only-provider.md).

## <a name="see-also"></a>Voir aussi

[Implémentation d’un fournisseur simple accessible en lecture seule](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
