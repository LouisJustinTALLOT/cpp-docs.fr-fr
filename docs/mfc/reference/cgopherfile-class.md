---
title: Classe CGopherFile
ms.date: 11/04/2016
f1_keywords:
- CGopherFile
- AFXINET/CGopherFile
- AFXINET/CGopherFile::CGopherFile
helpviewer_keywords:
- CGopherFile [MFC], CGopherFile
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
ms.openlocfilehash: e157a4509fe30b814a1834690a675906ac82afe7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373691"
---
# <a name="cgopherfile-class"></a>Classe CGopherFile

Fournit les fonctionnalités permettant de rechercher et de lire des fichiers sur un serveur Gopher.

> [!NOTE]
> Les `CGopherConnection`classes `CGopherFile` `CGopherFileFind`, `CGopherLocator` , et leurs membres ont été dépréciés parce qu’ils ne travaillent pas sur la plate-forme Windows XP, mais ils continueront à travailler sur des plates-formes antérieures.

## <a name="syntax"></a>Syntaxe

```
class CGopherFile : public CInternetFile
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CGopherFile::CGopherFile](#cgopherfile)|Construit un objet `CGopherFile`.|

## <a name="remarks"></a>Notes

Le service gopher ne permet pas aux utilisateurs d’écrire des données sur un fichier gopher car ce service fonctionne principalement comme une interface axée sur le menu pour trouver des informations. Les `CGopherFile` fonctions `Write` `WriteString`de `Flush` membre, , `CGopherFile`et ne sont pas mises en œuvre pour . Appelant ces fonctions `CGopherFile` sur un objet, renvoie un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Pour en savoir `CGopherFile` plus sur la façon dont fonctionne avec les autres classes Internet MFC, voir l’article [Internet Programming avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CGopherFile`

## <a name="requirements"></a>Spécifications

**En-tête:** afxinet.h

## <a name="cgopherfilecgopherfile"></a><a name="cgopherfile"></a>CGopherFile::CGopherFile

Cette fonction de membre `CGopherFile` est appelée à construire un objet.

```
CGopherFile(
    HINTERNET hFile,
    CGopherLocator& refLocator,
    CGopherConnection* pConnection);

CGopherFile(
    HINTERNET hFile,
    HINTERNET hSession,
    LPCTSTR pstrLocator,
    DWORD dwLocLen,
    DWORD_PTR dwContext);
```

### <a name="parameters"></a>Paramètres

*hFile (en)*<br/>
Une poignée à un fichier HINTERNET.

*refLocator*<br/>
Une référence à un objet [CGopherLocator.](../../mfc/reference/cgopherlocator-class.md)

*pConnection*<br/>
Un pointeur vers un objet [CGopherConnection.](../../mfc/reference/cgopherconnection-class.md)

*hSession*<br/>
Une poignée pour la session Internet en cours.

*pstrLocator (en)*<br/>
Un pointeur à une chaîne utilisée pour localiser le serveur gopher. Voir [Gopher Sessions](cgopherlocator-class.md) pour plus d’informations sur les localisateurs gopher.

*dwLocLen (en)*<br/>
Un DWORD contenant le nombre d’octets dans *pstrLocator*.

*dwContexte*<br/>
Un pointeur sur l’identifiant contextuelle du fichier en cours d’ouverture.

### <a name="remarks"></a>Notes

Vous avez `CGopherFile` besoin d’un objet à lire à partir d’un fichier lors d’une session Gopher Internet.

Vous ne `CGopherFile` créez jamais un objet directement. Au lieu de cela, appelez [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) pour ouvrir un fichier sur un serveur gopher.

## <a name="see-also"></a>Voir aussi

[Classe CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[Classe CInternetFile](../../mfc/reference/cinternetfile-class.md)<br/>
[Classe CGopherLocator](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFileFind, classe](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CGopherConnection, classe](../../mfc/reference/cgopherconnection-class.md)
