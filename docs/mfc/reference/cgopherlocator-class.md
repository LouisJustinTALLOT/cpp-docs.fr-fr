---
description: 'En savoir plus sur : classe CGopherLocator'
title: CGopherLocator, classe
ms.date: 11/04/2016
f1_keywords:
- CGopherLocator
- AFXINET/CGopherLocator
- AFXINET/CGopherLocator::CGopherLocator
- AFXINET/CGopherLocator::GetLocatorType
helpviewer_keywords:
- CGopherLocator [MFC], CGopherLocator
- CGopherLocator [MFC], GetLocatorType
ms.assetid: 6fcc015f-5ae6-4959-b936-858634c71019
ms.openlocfilehash: f615ce6fbda150d923f6664acff207fdebdbba3f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184021"
---
# <a name="cgopherlocator-class"></a>CGopherLocator, classe

Obtient un « localisateur » Gopher d’un serveur Gopher, détermine le type du localisateur et rend le localisateur disponible pour [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md).

> [!NOTE]
> Les classes `CGopherConnection` , `CGopherFile` , `CGopherFileFind` `CGopherLocator` et leurs membres ont été dépréciées, car elles ne fonctionnent pas sur la plateforme Windows XP, mais elles continuent de fonctionner sur les plateformes antérieures.

## <a name="syntax"></a>Syntaxe

```
class CGopherLocator : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CGopherLocator::CGopherLocator](#cgopherlocator)|Construit un objet `CGopherLocator`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CGopherLocator::GetLocatorType](#getlocatortype)|Analyse un localisateur Gopher et détermine ses attributs.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CGopherLocator :: Operator LPCTSTR](#operator_lpctstr)|Accède directement aux caractères stockés dans un `CGopherLocator` objet sous la forme d’une chaîne de style C.|

## <a name="remarks"></a>Notes

Une application doit obtenir un localisateur de serveur Gopher pour pouvoir récupérer des informations à partir de ce serveur. Une fois qu’il a le localisateur, il doit traiter le localisateur comme un jeton opaque.

Chaque localisateur Gopher possède des attributs qui déterminent le type de fichier ou de serveur trouvé. Pour obtenir la liste des types de localisateurs Gopher, consultez [GetLocatorType](#getlocatortype) .

Une application utilise normalement le localisateur pour les appels à [CGopherFileFind :: FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) pour récupérer une information spécifique.

Pour en savoir plus sur le `CGopherLocator` fonctionnement des autres classes Internet MFC, consultez l’article [programmation Internet avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CGopherLocator`

## <a name="requirements"></a>Spécifications

**En-tête :** AFXINET. h

## <a name="cgopherlocatorcgopherlocator"></a><a name="cgopherlocator"></a> CGopherLocator::CGopherLocator

Cette fonction membre est appelée pour créer un `CGopherLocator` objet.

```
CGopherLocator(const CGopherLocator& ref);
```

### <a name="parameters"></a>Paramètres

*ref*<br/>
Référence à un objet constant `CGopherLocator` .

### <a name="remarks"></a>Notes

Vous ne devez jamais créer un `CGopherLocator` objet directement. Au lieu de cela, appelez [CGopherConnection :: CreateLocator](../../mfc/reference/cgopherconnection-class.md#createlocator) pour créer et retourner un pointeur vers l' `CGopherLocator` objet.

## <a name="cgopherlocatorgetlocatortype"></a><a name="getlocatortype"></a> CGopherLocator::GetLocatorType

Appelez cette fonction membre pour récupérer le type de localisateur.

```
BOOL GetLocatorType(DWORD& dwRef) const;
```

### <a name="parameters"></a>Paramètres

*dwRef*<br/>
Référence à une valeur DWORD qui recevra le type de localisateur. Consultez la **section Notes** pour obtenir un tableau des types de localisateur.

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Les types possibles sont les suivants :

|Valeur|Signification|
|-----------|-------------|
|GOPHER_TYPE_TEXT_FILE|Fichier texte ASCII.|
|GOPHER_TYPE_DIRECTORY|Répertoire d’éléments Gopher supplémentaires.|
|GOPHER_TYPE_CSO|Un serveur d’annuaires téléphoniques CSO.|
|GOPHER_TYPE_ERROR|Indique une condition d’erreur.|
|GOPHER_TYPE_MAC_BINHEX|Fichier Macintosh au format BINHEX.|
|GOPHER_TYPE_DOS_ARCHIVE|Fichier d’archive DOS.|
|GOPHER_TYPE_UNIX_UUENCODED|Fichier UUENCODED.|
|GOPHER_TYPE_INDEX_SERVER|Un serveur d’index.|
|GOPHER_TYPE_TELNET|Un serveur Telnet.|
|GOPHER_TYPE_BINARY|Fichier binaire.|
|GOPHER_TYPE_REDUNDANT|Un serveur dupliqué. Les informations contenues dans sont un doublon du serveur principal. Le serveur principal est la dernière entrée de répertoire qui n’a pas de type de GOPHER_TYPE_REDUNDANT.|
|GOPHER_TYPE_TN3270|Un serveur TN3270.|
|GOPHER_TYPE_GIF|Fichier graphique GIF.|
|GOPHER_TYPE_IMAGE|Fichier image.|
|GOPHER_TYPE_BITMAP|Fichier bitmap.|
|GOPHER_TYPE_MOVIE|Fichier vidéo.|
|GOPHER_TYPE_SOUND|Fichier audio.|
|GOPHER_TYPE_HTML|Document HTML.|
|GOPHER_TYPE_PDF|Fichier PDF.|
|GOPHER_TYPE_CALENDAR|Fichier de calendrier.|
|GOPHER_TYPE_INLINE|Fichier Inline.|
|GOPHER_TYPE_UNKNOWN|Le type d’élément est inconnu.|
|GOPHER_TYPE_ASK|Un élément Ask +.|
|GOPHER_TYPE_GOPHER_PLUS|Un élément Gopher +.|

## <a name="cgopherlocatoroperator-lpctstr"></a><a name="operator_lpctstr"></a> CGopherLocator :: Operator LPCTSTR

Cet opérateur de cast utile fournit une méthode efficace pour accéder à la chaîne C se terminant par un caractère null contenue dans un `CGopherLocator` objet.

```
operator LPCTSTR () const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur de caractère vers les données de la chaîne.

### <a name="remarks"></a>Notes

Aucun caractère n’est copié ; seul un pointeur est retourné.

## <a name="see-also"></a>Voir aussi

[CObject (classe)](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind, classe](../../mfc/reference/cgopherfilefind-class.md)
