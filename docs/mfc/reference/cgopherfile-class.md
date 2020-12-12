---
description: 'En savoir plus sur : classe CGopherFile'
title: CGopherFile, classe
ms.date: 11/04/2016
f1_keywords:
- CGopherFile
- AFXINET/CGopherFile
- AFXINET/CGopherFile::CGopherFile
helpviewer_keywords:
- CGopherFile [MFC], CGopherFile
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
ms.openlocfilehash: 8f511bdaf3ae6417972ea19465c0392832a2b408
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184073"
---
# <a name="cgopherfile-class"></a>CGopherFile, classe

Fournit les fonctionnalités permettant de rechercher et de lire des fichiers sur un serveur Gopher.

> [!NOTE]
> Les classes `CGopherConnection` , `CGopherFile` , `CGopherFileFind` `CGopherLocator` et leurs membres ont été dépréciées, car elles ne fonctionnent pas sur la plateforme Windows XP, mais elles continuent de fonctionner sur les plateformes antérieures.

## <a name="syntax"></a>Syntaxe

```
class CGopherFile : public CInternetFile
```

## <a name="members"></a>Membres

### <a name="protected-constructors"></a>Constructeurs protégés

|Nom|Description|
|----------|-----------------|
|[CGopherFile :: CGopherFile](#cgopherfile)|Construit un objet `CGopherFile`.|

## <a name="remarks"></a>Notes

Le service Gopher n’autorise pas les utilisateurs à écrire des données dans un fichier Gopher, car ce service fonctionne principalement comme une interface pilotée par menus pour la recherche d’informations. Les `CGopherFile` fonctions membres `Write` , `WriteString` et ne `Flush` sont pas implémentées pour `CGopherFile` . L’appel de ces fonctions sur un `CGopherFile` objet retourne un [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Pour en savoir plus sur le `CGopherFile` fonctionnement des autres classes Internet MFC, consultez l’article [programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CGopherFile`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXINET. h

## <a name="cgopherfilecgopherfile"></a><a name="cgopherfile"></a> CGopherFile :: CGopherFile

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
Handle d’un fichier HINTERNET.

*refLocator*<br/>
Référence à un objet [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) .

*pConnection*<br/>
Pointeur vers un objet [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) .

*hSession*<br/>
Handle de la session Internet en cours.

*pstrLocator*<br/>
Pointeur vers une chaîne utilisée pour localiser le serveur Gopher. Pour plus d’informations sur les localisateurs Gopher, consultez [sessions Gopher](cgopherlocator-class.md) .

*dwLocLen*<br/>
Valeur DWORD contenant le nombre d’octets dans *pstrLocator*.

*dwContext*<br/>
Pointeur vers l’identificateur de contexte du fichier en cours d’ouverture.

### <a name="remarks"></a>Notes

Vous avez besoin d’un `CGopherFile` objet pour lire un fichier lors d’une session Internet Gopher.

Vous ne devez jamais créer un `CGopherFile` objet directement. Au lieu de cela, appelez [CGopherConnection :: OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) pour ouvrir un fichier sur un serveur Gopher.

## <a name="see-also"></a>Voir aussi

[CInternetFile, classe](../../mfc/reference/cinternetfile-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CInternetFile, classe](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherLocator, classe](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFileFind, classe](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CGopherConnection, classe](../../mfc/reference/cgopherconnection-class.md)
