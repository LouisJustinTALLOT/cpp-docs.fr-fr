---
title: CGopherFile (classe)
ms.date: 11/04/2016
f1_keywords:
- CGopherFile
- AFXINET/CGopherFile
- AFXINET/CGopherFile::CGopherFile
helpviewer_keywords:
- CGopherFile [MFC], CGopherFile
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
ms.openlocfilehash: 9bb242cb53593862cb51e0c193eb739625127adc
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285189"
---
# <a name="cgopherfile-class"></a>CGopherFile (classe)

Fournit les fonctionnalités permettant de rechercher et de lire des fichiers sur un serveur Gopher.

> [!NOTE]
>  Les classes `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` et leurs membres ont été déconseillées, car ils ne fonctionnent pas sur la plate-forme Windows XP, mais ils continueront à fonctionner sur des plateformes antérieures.

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

Le service gopher n’autorise pas les utilisateurs à écrire des données dans un fichier gopher, car ce service fonctionne principalement comme une interface à menus pour trouver des informations. Le `CGopherFile` fonctions membres `Write`, `WriteString`, et `Flush` ne sont pas implémentées pour `CGopherFile`. Appel de ces fonctions sur un `CGopherFile` de l’objet, retourne un [exception CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Pour en savoir plus sur la façon `CGopherFile` fonctionne avec les autres classes Internet de MFC, consultez l’article [Internet programmation avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CGopherFile`

## <a name="requirements"></a>Spécifications

**En-tête :** afxinet.h

##  <a name="cgopherfile"></a>  CGopherFile::CGopherFile

Cette fonction membre est appelée pour construire un `CGopherFile` objet.

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

*hFile*<br/>
Handle vers un fichier HINTERNET.

*refLocator*<br/>
Une référence à un [objet CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objet.

*pConnection*<br/>
Un pointeur vers un [objet CGopherConnection](../../mfc/reference/cgopherconnection-class.md) objet.

*hSession*<br/>
Handle vers la session Internet actuel.

*pstrLocator*<br/>
Un pointeur vers une chaîne utilisée pour rechercher le serveur gopher. Consultez [Gopher Sessions](cgopherlocator-class.md) pour plus d’informations sur les localisateurs gopher.

*dwLocLen*<br/>
Une valeur DWORD qui contient le nombre d’octets dans *pstrLocator*.

*dwContext*<br/>
Pointeur vers l’identificateur de contexte du fichier en cours d’ouverture.

### <a name="remarks"></a>Notes

Vous devez un `CGopherFile` objet à lire à partir d’un fichier pendant une session d’Internet gopher.

Vous ne créez jamais un `CGopherFile` directement l’objet. Au lieu de cela, appelez [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) pour ouvrir un fichier sur un serveur gopher.

## <a name="see-also"></a>Voir aussi

[CInternetFile, classe](../../mfc/reference/cinternetfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CInternetFile, classe](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherLocator, classe](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFileFind, classe](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CGopherConnection, classe](../../mfc/reference/cgopherconnection-class.md)
