---
title: Lecture de chaînes dans le fournisseur OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, reading strings into
ms.assetid: 517f322c-f37e-4eed-bf5e-dd9a412c2f98
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 88272c935c3e610ee633a1e076a2d2d76b5840f2
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082564"
---
# <a name="reading-strings-into-the-ole-db-provider"></a>Lecture de chaînes dans le fournisseur OLE DB

Le `RMyProviderRowset::Execute` fonction ouvre un fichier et lit les chaînes. Le consommateur passe le nom de fichier au fournisseur en appelant [ICommandText::SetCommandText](/previous-versions/windows/desktop/ms709757). Le fournisseur reçoit le nom de fichier et le stocke dans la variable membre `m_szCommandText`. `Execute` lit le nom de fichier à partir de `m_szCommandText`. Si le nom de fichier n’est pas valide ou le fichier n’est pas disponible, `Execute` retourne une erreur. Sinon, il ouvre le fichier et appelle `fgets` pour récupérer les chaînes. Pour chaque jeu de chaînes qu’il lit, `Execute` crée une instance de l’enregistrement utilisateur (`CAgentMan`) et le place dans un tableau.  
  
Si le fichier ne peut pas être ouvert, `Execute` doit retourner DB_E_NOTABLE. Si elle retourne E_FAIL à la place, le fournisseur ne fonctionnera pas avec beaucoup de consommateurs et ne peut pas passer de OLE DB [tests de compatibilité](../../data/oledb/testing-your-provider.md).  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  

Le texte modifié `Execute` fonction ressemble à ceci :  
  
### <a name="code"></a>Code  
  
```cpp
/////////////////////////////////////////////////////////////////////////  
// MyProviderRS.h  
class RMyProviderRowset : public CRowsetImpl< RMyProviderRowset, CAgentMan, CRMyProviderCommand>  
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
        size_t nLength;        errcodeerr;  
  
        ObjectLock lock(this);  
  
        // From a filename, passed in as a command text, scan the file  
        // placing data in the data array.  
        if (!m_szCommandText)  
        {  
            ATLTRACE("No filename specified");  
            return E_FAIL;  
        }  
  
        // Open the file  
        _tcscpy_s(szFile, sizeOfFile, m_szCommandText);  
        if (szFile[0] == _T('\0') ||   
            ((err = fopen_s(&pFile, &szFile[0], "r")) == 0))  
        {  
            ATLTRACE("Could not open file");  
            return DB_E_NOTABLE;  
        }  
  
        // Scan and parse the file.  
        // The file should contain two strings per record  
        LONG cFiles = 0;  
        while (fgets(szString, sizeOfBuffer, pFile) != NULL)  
        {  
            nLength = strnlen(szString, sizeOfBuffer);  
            szString[nLength-1] = '\0';   // Strip off trailing CR/LF  
            CAgentMan am;  
            _tcscpy_s(am.szCommand, am.sizeOfCommand, szString);  
            _tcscpy_s(am.szCommand2, am.sizeOfCommand2, szString);  
  
            if (fgets(szString, sizeOfBuffer, pFile) != NULL)  
            {  
                nLength = strnlen(szString, sizeOfBuffer);  
                szString[nLength-1] = '\0'; // Strip off trailing CR/LF  
                _tcscpy_s(am.szText, am.sizeOfText, szString);  
                _tcscpy_s(am.szText2, am.sizeOfText2, szString);  
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
}  
```  
  
## <a name="see-also"></a>Voir aussi  

[Implémentation d’un fournisseur simple accessible en lecture seule](../../data/oledb/implementing-the-simple-read-only-provider.md)