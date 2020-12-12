---
description: 'En savoir plus sur : lecture de chaînes dans le fournisseur OLE DB'
title: Lecture de chaînes dans le fournisseur OLE DB
ms.date: 10/13/2018
helpviewer_keywords:
- OLE DB providers, reading strings into
ms.assetid: 517f322c-f37e-4eed-bf5e-dd9a412c2f98
ms.openlocfilehash: 5df8812d5589dd457684bf5e36a8a49f798f99aa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286629"
---
# <a name="reading-strings-into-the-ole-db-provider"></a>Lecture de chaînes dans le fournisseur OLE DB

La `CCustomRowset::Execute` fonction ouvre un fichier et lit les chaînes. Le consommateur transmet le nom de fichier au fournisseur en appelant [ICommandText :: SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)). Le fournisseur reçoit le nom de fichier et le stocke dans la variable membre `m_strCommandText` . `Execute` lit le nom de fichier à partir de `m_strCommandText` . Si le nom de fichier n’est pas valide ou si le fichier n’est pas disponible, `Execute` retourne une erreur. Dans le cas contraire, il ouvre le fichier et appelle `fgets` pour récupérer les chaînes. Pour chaque ensemble de chaînes qu’il lit, `Execute` crée une instance de l’enregistrement utilisateur (modifié `CCustomWindowsFile` à partir du [stockage des chaînes dans le fournisseur OLE DB](../../data/oledb/storing-strings-in-the-ole-db-provider.md)) et le place dans un tableau.

Si le fichier ne peut pas être ouvert, `Execute` doit retourner DB_E_NOTABLE. S’il retourne E_FAIL à la place, le fournisseur ne fonctionnera pas avec de nombreux consommateurs et ne passera pas les [tests de conformité](../../data/oledb/testing-your-provider.md)OLE DB.

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

Une fois cette opération effectuée, votre fournisseur doit être prêt à être compilé et exécuté. Pour tester le fournisseur, vous avez besoin d’un consommateur avec une fonctionnalité de correspondance. L' [implémentation d’un consommateur simple](../../data/oledb/implementing-a-simple-consumer.md) montre comment créer un tel consommateur de test. Exécutez le consommateur de test avec le fournisseur et vérifiez que le consommateur de test récupère les chaînes appropriées auprès du fournisseur.

Une fois que vous avez testé votre fournisseur, vous souhaiterez peut-être améliorer ses fonctionnalités en implémentant des interfaces supplémentaires. Un exemple est présenté dans [amélioration du fournisseur de Read-Only simple](../../data/oledb/enhancing-the-simple-read-only-provider.md).

## <a name="see-also"></a>Voir aussi

[Implémentation du fournisseur de Read-Only simple](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
