---
title: Classe CGopherLocator
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
ms.openlocfilehash: d23ef3dad68c62e74ec64454953ca372b8c31114
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373666"
---
# <a name="cgopherlocator-class"></a>Classe CGopherLocator

Obtient un gopher "locateur" à partir d’un serveur gopher, détermine le type du localisateur, et rend le localisateur disponible pour [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md).

> [!NOTE]
> Les `CGopherConnection`classes `CGopherFile` `CGopherFileFind`, `CGopherLocator` , et leurs membres ont été dépréciés parce qu’ils ne travaillent pas sur la plate-forme Windows XP, mais ils continueront à travailler sur des plates-formes antérieures.

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
|[CGopherLocator::GetLocatorType](#getlocatortype)|Parse un repérage de gopher et détermine ses attributs.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CGopherLocator::opérateur LPCTSTR](#operator_lpctstr)|Accéde directement aux `CGopherLocator` caractères stockés dans un objet sous forme de chaîne de style C.|

## <a name="remarks"></a>Notes

Une application doit obtenir le repérage d’un serveur gopher avant qu’il puisse récupérer des informations à partir de ce serveur. Une fois qu’il a le localisateur, il doit traiter le localisateur comme un jeton opaque.

Chaque repérage gopher a des attributs qui déterminent le type de fichier ou de serveur trouvé. Consultez [GetLocatorType](#getlocatortype) pour une liste de types de localisateurs gopher.

Une application utilise normalement le localisateur pour les appels à [CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) pour récupérer un élément spécifique de l’information.

Pour en savoir `CGopherLocator` plus sur la façon dont fonctionne avec les autres classes Internet MFC, voir l’article [Internet Programming avec WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CGopherLocator`

## <a name="requirements"></a>Spécifications

**En-tête:** afxinet.h

## <a name="cgopherlocatorcgopherlocator"></a><a name="cgopherlocator"></a>CGopherLocator::CGopherLocator

Cette fonction de membre `CGopherLocator` est appelée pour créer un objet.

```
CGopherLocator(const CGopherLocator& ref);
```

### <a name="parameters"></a>Paramètres

*ref*<br/>
Une référence à `CGopherLocator` un objet constant.

### <a name="remarks"></a>Notes

Vous ne `CGopherLocator` créez jamais un objet directement. Au lieu de cela, appelez [CGopherConnection:CreateLocator](../../mfc/reference/cgopherconnection-class.md#createlocator) `CGopherLocator` pour créer et retourner un pointeur à l’objet.

## <a name="cgopherlocatorgetlocatortype"></a><a name="getlocatortype"></a>CGopherLocator::GetLocatorType

Appelez cette fonction de membre pour obtenir le type de localisation.

```
BOOL GetLocatorType(DWORD& dwRef) const;
```

### <a name="parameters"></a>Paramètres

*dwRef (en)*<br/>
Une référence à un DWORD qui recevra le type de repérage. Voir **Remarques** pour une table de types de localisation.

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro cas de réussite ; sinon, 0. Si l’appel échoue, la fonction Win32 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) peut être appelée pour déterminer la cause de l’erreur.

### <a name="remarks"></a>Notes

Les types possibles sont les suivants :

|Valeur|Signification|
|-----------|-------------|
|GOPHER_TYPE_TEXT_FILE|Un fichier texte ASCII.|
|GOPHER_TYPE_DIRECTORY|Un répertoire d’articles Gopher supplémentaires.|
|GOPHER_TYPE_CSO|Un serveur de annuaire téléphonique CSO.|
|GOPHER_TYPE_ERROR|Indique une condition d’erreur.|
|GOPHER_TYPE_MAC_BINHEX|Un fichier Macintosh en format BINHEX.|
|GOPHER_TYPE_DOS_ARCHIVE|Un fichier d’archives DOS.|
|GOPHER_TYPE_UNIX_UUENCODED|Un fichier UUENCODED.|
|GOPHER_TYPE_INDEX_SERVER|Un serveur d’index.|
|GOPHER_TYPE_TELNET|Un serveur Telnet.|
|GOPHER_TYPE_BINARY|Un fichier binaire.|
|GOPHER_TYPE_REDUNDANT|Un serveur dupliqué. Les informations contenues dans est un double du serveur principal. Le serveur principal est la dernière entrée d’annuaire qui n’avait pas de type GOPHER_TYPE_REDUNDANT.|
|GOPHER_TYPE_TN3270|Un serveur TN3270.|
|GOPHER_TYPE_GIF|Un fichier graphique GIF.|
|GOPHER_TYPE_IMAGE|Un fichier d’image.|
|GOPHER_TYPE_BITMAP|Un fichier de bitmap.|
|GOPHER_TYPE_MOVIE|Un fichier de film.|
|GOPHER_TYPE_SOUND|Un fichier sonore.|
|GOPHER_TYPE_HTML|Document HTML.|
|GOPHER_TYPE_PDF|Un fichier PDF.|
|GOPHER_TYPE_CALENDAR|Un fichier calendrier.|
|GOPHER_TYPE_INLINE|Un fichier en ligne.|
|GOPHER_TYPE_UNKNOWN|Le type d’élément est inconnu.|
|GOPHER_TYPE_ASK|Un article AskMD.|
|GOPHER_TYPE_GOPHER_PLUS|Un article GopherMD.|

## <a name="cgopherlocatoroperator-lpctstr"></a><a name="operator_lpctstr"></a>CGopherLocator::opérateur LPCTSTR

Cet opérateur de moulage utile fournit une méthode efficace `CGopherLocator` pour accéder à la chaîne C non terminée contenue dans un objet.

```
operator LPCTSTR () const;
```

### <a name="return-value"></a>Valeur de retour

Un pointeur de caractère aux données de la chaîne.

### <a name="remarks"></a>Notes

Aucun personnage n’est copié; seul un pointeur est retourné.

## <a name="see-also"></a>Voir aussi

[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind, classe](../../mfc/reference/cgopherfilefind-class.md)
