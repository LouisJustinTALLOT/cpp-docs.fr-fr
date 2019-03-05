---
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
ms.openlocfilehash: 79adbf126438c7d9f2884987c53b573991f92cf1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57291378"
---
# <a name="cgopherlocator-class"></a>CGopherLocator, classe

Obtient un « localisateur » d’un serveur gopher, détermine le type du localisateur et rend le localisateur accessible à [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md).

> [!NOTE]
>  Les classes `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` et leurs membres ont été déconseillées, car ils ne fonctionnent pas sur la plate-forme Windows XP, mais ils continueront à fonctionner sur des plateformes antérieures.

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
|[CGopherLocator::GetLocatorType](#getlocatortype)|Analyse un localisateur gopher et détermine ses attributs.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CGopherLocator::operator LPCTSTR](#operator_lpctstr)|Accède directement aux caractères stockés dans un `CGopherLocator` objet sous la forme d’une chaîne de style C.|

## <a name="remarks"></a>Notes

Une application doit obtenir les recherche d’un serveur gopher avant d’extraire des informations à partir de ce serveur. Une fois qu’il a le localisateur, il doit traiter le localisateur comme un jeton opaque.

Chaque localisateur gopher a des attributs qui déterminent le type de fichier ou le serveur a été trouvé. Consultez [GetLocatorType](#getlocatortype) pour obtenir la liste des types de localisateurs de gopher.

Une application utilise normalement le localisateur pour les appels à [CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) pour récupérer une information spécifique.

Pour en savoir plus sur la façon `CGopherLocator` fonctionne avec les autres classes Internet de MFC, consultez l’article [Internet programmation avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CGopherLocator`

## <a name="requirements"></a>Spécifications

**En-tête :** afxinet.h

##  <a name="cgopherlocator"></a>  CGopherLocator::CGopherLocator

Cette fonction membre est appelée pour créer un `CGopherLocator` objet.

```
CGopherLocator(const CGopherLocator& ref);
```

### <a name="parameters"></a>Paramètres

*ref*<br/>
Une référence à une constante `CGopherLocator` objet.

### <a name="remarks"></a>Notes

Vous ne créez jamais un `CGopherLocator` directement l’objet. Au lieu de cela, appelez [CGopherConnection::CreateLocator](../../mfc/reference/cgopherconnection-class.md#createlocator) pour créer et retourner un pointeur vers le `CGopherLocator` objet.

##  <a name="getlocatortype"></a>  CGopherLocator::GetLocatorType

Appelez cette fonction membre pour obtenir le type de localisateur.

```
BOOL GetLocatorType(DWORD& dwRef) const;
```

### <a name="parameters"></a>Paramètres

*dwRef*<br/>
Une référence à une valeur DWORD qui recevra le type de localisateur. Consultez **remarques** pour un tableau de types de localisateur.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Les types possibles sont les suivantes :

|Value|Signification|
|-----------|-------------|
|GOPHER_TYPE_TEXT_FILE|Un fichier texte ASCII.|
|GOPHER_TYPE_DIRECTORY|Un répertoire d’éléments Gopher supplémentaires.|
|GOPHER_TYPE_CSO|Un serveur d’annuaire téléphonique CSO.|
|GOPHER_TYPE_ERROR|Indique une condition d’erreur.|
|GOPHER_TYPE_MAC_BINHEX|Un fichier Macintosh au format BINHEX.|
|GOPHER_TYPE_DOS_ARCHIVE|Un fichier d’archive DOS.|
|GOPHER_TYPE_UNIX_UUENCODED|Un fichier UUEncode.|
|GOPHER_TYPE_INDEX_SERVER|Un serveur d’index.|
|GOPHER_TYPE_TELNET|Un serveur Telnet.|
|GOPHER_TYPE_BINARY|Un fichier binaire.|
|GOPHER_TYPE_REDUNDANT|Un serveur en double. Les informations contenues dans sont un doublon du serveur principal. Le serveur principal est la dernière entrée de répertoire qui n’avait pas d’un type GOPHER_TYPE_REDUNDANT.|
|GOPHER_TYPE_TN3270|Un serveur TN3270.|
|GOPHER_TYPE_GIF|Un fichier graphique GIF.|
|GOPHER_TYPE_IMAGE|Un fichier image.|
|GOPHER_TYPE_BITMAP|Un fichier bitmap.|
|GOPHER_TYPE_MOVIE|Un fichier vidéo.|
|GOPHER_TYPE_SOUND|Un fichier audio.|
|GOPHER_TYPE_HTML|Document HTML.|
|GOPHER_TYPE_PDF|Un fichier PDF.|
|GOPHER_TYPE_CALENDAR|Un fichier de calendrier.|
|GOPHER_TYPE_INLINE|Un fichier inline.|
|GOPHER_TYPE_UNKNOWN|Le type d’élément est inconnu.|
|GOPHER_TYPE_ASK|Un élément clé Ask +.|
|GOPHER_TYPE_GOPHER_PLUS|Un élément Gopher +.|

##  <a name="operator_lpctstr"></a>  CGopherLocator::operator LPCTSTR

Cet opérateur de cast utile fournit une méthode efficace pour accéder à la chaîne C se terminant par null est contenue dans un `CGopherLocator` objet.

```
operator LPCTSTR () const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur de caractère pour les données de la chaîne.

### <a name="remarks"></a>Notes

Aucuns caractères ne sont copiés ; uniquement un pointeur est retourné.

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind, classe](../../mfc/reference/cgopherfilefind-class.md)
