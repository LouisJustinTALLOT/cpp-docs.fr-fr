---
title: Cpatht, classe
ms.date: 03/27/2019
f1_keywords:
- CPathT
- ATLPATH/ATL::CPathT
- ATLPATH/ATL::CPathT::PCXSTR
- ATLPATH/ATL::CPathT::PXSTR
- ATLPATH/ATL::CPathT::XCHAR
- ATLPATH/ATL::CPathT::CPathT
- ATLPATH/ATL::CPathT::AddBackslash
- ATLPATH/ATL::CPathT::AddExtension
- ATLPATH/ATL::CPathT::Append
- ATLPATH/ATL::CPathT::BuildRoot
- ATLPATH/ATL::CPathT::Canonicalize
- ATLPATH/ATL::CPathT::Combine
- ATLPATH/ATL::CPathT::CommonPrefix
- ATLPATH/ATL::CPathT::CompactPath
- ATLPATH/ATL::CPathT::CompactPathEx
- ATLPATH/ATL::CPathT::FileExists
- ATLPATH/ATL::CPathT::FindExtension
- ATLPATH/ATL::CPathT::FindFileName
- ATLPATH/ATL::CPathT::GetDriveNumber
- ATLPATH/ATL::CPathT::GetExtension
- ATLPATH/ATL::CPathT::IsDirectory
- ATLPATH/ATL::CPathT::IsFileSpec
- ATLPATH/ATL::CPathT::IsPrefix
- ATLPATH/ATL::CPathT::IsRelative
- ATLPATH/ATL::CPathT::IsRoot
- ATLPATH/ATL::CPathT::IsSameRoot
- ATLPATH/ATL::CPathT::IsUNC
- ATLPATH/ATL::CPathT::IsUNCServer
- ATLPATH/ATL::CPathT::IsUNCServerShare
- ATLPATH/ATL::CPathT::MakePretty
- ATLPATH/ATL::CPathT::MatchSpec
- ATLPATH/ATL::CPathT::QuoteSpaces
- ATLPATH/ATL::CPathT::RelativePathTo
- ATLPATH/ATL::CPathT::RemoveArgs
- ATLPATH/ATL::CPathT::RemoveBackslash
- ATLPATH/ATL::CPathT::RemoveBlanks
- ATLPATH/ATL::CPathT::RemoveExtension
- ATLPATH/ATL::CPathT::RemoveFileSpec
- ATLPATH/ATL::CPathT::RenameExtension
- ATLPATH/ATL::CPathT::SkipRoot
- ATLPATH/ATL::CPathT::StripPath
- ATLPATH/ATL::CPathT::StripToRoot
- ATLPATH/ATL::CPathT::UnquoteSpaces
- ATLPATH/ATL::CPathT::m_strPath
helpviewer_keywords:
- CPathT class
ms.assetid: eba4137d-1fd2-4b44-a2e1-0944db64df3c
ms.openlocfilehash: 109f9baefd0e6775db05eeba8cb78542bf60a9ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62278174"
---
# <a name="cpatht-class"></a>Cpatht, classe

Cette classe représente un chemin d’accès.

> [!IMPORTANT]
> Cette classe et ses membres ne peut pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <typename StringType>
class CPathT
```

#### <a name="parameters"></a>Paramètres

*StringType*<br/>
La classe de chaîne ATL/MFC à utiliser pour le chemin d’accès (consultez [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)).

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CPathT::PCXSTR](#pcxstr)|Un type de chaîne constante.|
|[CPathT::PXSTR](#pxstr)|Un type chaîne.|
|[CPathT::XCHAR](#xchar)|Type de caractère.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CPathT::CPathT](#cpatht)|Le constructeur pour le chemin d’accès.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPathT::AddBackslash](#addbackslash)|Appelez cette méthode pour ajouter une barre oblique inverse à la fin d’une chaîne pour créer la syntaxe correcte pour un chemin d’accès.|
|[CPathT::AddExtension](#addextension)|Appelez cette méthode pour ajouter une extension de fichier à un chemin d’accès.|
|[CPathT::Append](#append)|Appelez cette méthode pour ajouter une chaîne pour le chemin d’accès actuel.|
|[CPathT::BuildRoot](#buildroot)|Appelez cette méthode pour créer un chemin d’accès racine à partir d’un nombre donné de lecteur.|
|[CPathT::Canonicalize](#canonicalize)|Appelez cette méthode pour convertir le chemin d’accès de la forme canonique.|
|[CPathT::Combine](#combine)|Appelez cette méthode pour concaténer une chaîne représentant un nom de répertoire et une chaîne représentant un nom de chemin d’accès de fichier dans un chemin d’accès.|
|[CPathT::CommonPrefix](#commonprefix)|Appelez cette méthode pour déterminer si le chemin d’accès spécifié partage un préfixe commun avec le chemin d’accès actuel.|
|[CPathT::CompactPath](#compactpath)|Appelez cette méthode pour tronquer un chemin d’accès de fichier d’ajuster au sein d’une largeur en pixels donné en remplacement des composants de chemin d’accès avec les points de suspension.|
|[CPathT::CompactPathEx](#compactpathex)|Appelez cette méthode pour tronquer un chemin d’accès de fichier d’ajuster au sein d’un nombre donné de caractères en remplacement des composants de chemin d’accès avec les points de suspension.|
|[CPathT::FileExists](#fileexists)|Appelez cette méthode pour vérifier si le fichier à ce nom de chemin d’accès existe.|
|[CPathT::FindExtension](#findextension)|Appelez cette méthode pour rechercher la position de l’extension de fichier dans le chemin d’accès.|
|[CPathT::FindFileName](#findfilename)|Appelez cette méthode pour trouver la position du nom de fichier dans le chemin d’accès.|
|[CPathT::GetDriveNumber](#getdrivenumber)|Appelez cette méthode pour rechercher le chemin d’accès pour une lettre de lecteur dans la plage de 'A' à 'Z' et retourner le nombre de lecteur correspondante.|
|[CPathT::GetExtension](#getextension)|Appelez cette méthode pour obtenir l’extension de fichier dans le chemin d’accès.|
|[CPathT::IsDirectory](#isdirectory)|Appelez cette méthode pour vérifier si le chemin d’accès est un répertoire valide.|
|[CPathT::IsFileSpec](#isfilespec)|Appelez cette méthode pour rechercher un chemin d’accès pour tout caractère délimiteur de chemin d’accès (par exemple, ' :' ou '\\'). S’il n’y a aucun caractère délimiteur de chemin d’accès est présent, le chemin d’accès est considéré comme un chemin d’accès de la spécification de fichier.|
|[CPathT::IsPrefix](#isprefix)|Appelez cette méthode pour déterminer si un chemin d’accès contient un préfixe valide du type passé *pszPrefix*.|
|[CPathT::IsRelative](#isrelative)|Appelez cette méthode pour déterminer si le chemin d’accès est relatif.|
|[CPathT::IsRoot](#isroot)|Appelez cette méthode pour déterminer si le chemin d’accès est un répertoire racine.|
|[CPathT::IsSameRoot](#issameroot)|Appelez cette méthode pour déterminer si un autre chemin d’accès est un composant racine commun avec le chemin d’accès actuel.|
|[CPathT::IsUNC](#isunc)|Appelez cette méthode pour déterminer si le chemin d’accès est un chemin d’accès UNC (convention universelle d’affectation de noms) valide pour un serveur et le partager.|
|[CPathT::IsUNCServer](#isuncserver)|Appelez cette méthode pour déterminer si le chemin d’accès est un chemin d’accès UNC (convention universelle d’affectation de noms) valide pour un seul serveur.|
|[CPathT::IsUNCServerShare](#isuncservershare)|Appelez cette méthode pour déterminer si le chemin d’accès est un chemin de partage UNC (convention universelle d’affectation de noms) valid, \\ \  *server*\ *partager*.|
|[CPathT::MakePretty](#makepretty)|Appelez cette méthode pour convertir un chemin d’accès à tous les caractères minuscules pour donner le chemin d’accès une apparence cohérente.|
|[CPathT::MatchSpec](#matchspec)|Appelez cette méthode pour rechercher le chemin d’accès d’une chaîne contenant un type de correspondance de caractère générique.|
|[CPathT::QuoteSpaces](#quotespaces)|Appelez cette méthode pour délimiter le chemin d’accès entre guillemets s’il contient des espaces.|
|[CPathT::RelativePathTo](#relativepathto)|Appelez cette méthode pour créer un chemin d’accès relatif d’un fichier ou dossier à un autre.|
|[CPathT::RemoveArgs](#removeargs)|Appelez cette méthode pour supprimer tous les arguments de ligne de commande à partir du chemin.|
|[CPathT::RemoveBackslash](#removebackslash)|Appelez cette méthode pour supprimer la barre oblique de fin du chemin d’accès.|
|[CPathT::RemoveBlanks](#removeblanks)|Appelez cette méthode pour supprimer tous les espaces de début et de fin du chemin d’accès.|
|[CPathT::RemoveExtension](#removeextension)|Appelez cette méthode pour supprimer l’extension de fichier du chemin d’accès, le cas échéant.|
|[CPathT::RemoveFileSpec](#removefilespec)|Appelez cette méthode pour supprimer le nom de fichier à droite et la barre oblique inverse à partir du chemin, s’il a les.|
|[CPathT::RenameExtension](#renameextension)|Appelez cette méthode pour remplacer l’extension de nom de fichier dans le chemin d’accès avec une nouvelle extension. Si le nom de fichier ne contient pas une extension, l’extension sera attachée à la fin de la chaîne.|
|[CPathT::SkipRoot](#skiproot)|Appelez cette méthode pour analyser un chemin d’accès, en ignorant la lettre de lecteur ou les parties de chemin d’accès UNC/partage de serveur.|
|[CPathT::StripPath](#strippath)|Appelez cette méthode pour supprimer la partie de chemin d’accès d’un chemin d’accès complet et le nom de fichier.|
|[CPathT::StripToRoot](#striptoroot)|Appelez cette méthode pour supprimer toutes les parties du chemin d’accès à l’exception des informations sur les racine.|
|[CPathT::UnquoteSpaces](#unquotespaces)|Appelez cette méthode pour supprimer les guillemets de début et de fin d’un chemin d’accès.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[StringType const CPathT::operator &](#operator_const_stringtype_amp)|Cet opérateur permet à l’objet à être traitée comme une chaîne.|
|[CPathT::operator CPathT::PCXSTR](#operator_cpatht__pcxstr)|Cet opérateur permet à l’objet à être traitée comme une chaîne.|
|[CPathT::operator StringType &](#operator_stringtype_amp)|Cet opérateur permet à l’objet à être traitée comme une chaîne.|
|[CPathT::operator +=](#operator_add_eq)|Cet opérateur ajoute une chaîne pour le chemin d’accès.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPathT::m_strPath](#m_strpath)|Chemin d’accès.|

## <a name="remarks"></a>Notes

`CPath`, `CPathA`, et `CPathW` sont des instanciations du `CPathT` définie comme suit :

`typedef CPathT< CString > CPath;`

`typedef CPathT< CStringA > CPathA;`

`typedef CPathT< CStringW > CPathW;`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlpath.h

##  <a name="addbackslash"></a>  CPathT::AddBackslash

Appelez cette méthode pour ajouter une barre oblique inverse à la fin d’une chaîne pour créer la syntaxe correcte pour un chemin d’accès. Si le chemin d’accès a déjà une barre oblique de fin, aucune barre oblique inverse n’est ajoutée.

```
void AddBackslash();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathAddBackSlash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha).

##  <a name="addextension"></a>  CPathT::AddExtension

Appelez cette méthode pour ajouter une extension de fichier à un chemin d’accès.

```
BOOL AddExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Paramètres

*pszExtension*<br/>
L’extension de fichier à ajouter.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona).

##  <a name="append"></a>  CPathT::Append

Appelez cette méthode pour ajouter une chaîne pour le chemin d’accès actuel.

```
BOOL Append(PCXSTR pszMore);
```

### <a name="parameters"></a>Paramètres

*pszMore*<br/>
Chaîne à ajouter.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda).

##  <a name="buildroot"></a>  CPathT::BuildRoot

Appelez cette méthode pour créer un chemin d’accès racine à partir d’un nombre donné de lecteur.

```
void BuildRoot(int iDrive);
```

### <a name="parameters"></a>Paramètres

*iDrive*<br/>
Le numéro du lecteur (0 est a, 1 b : et ainsi de suite).

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota).

##  <a name="canonicalize"></a>  CPathT::Canonicalize

Appelez cette méthode pour convertir le chemin d’accès de la forme canonique.

```
void Canonicalize();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea).

##  <a name="combine"></a>  CPathT::Combine

Appelez cette méthode pour concaténer une chaîne représentant un nom de répertoire et une chaîne représentant un nom de chemin d’accès de fichier dans un chemin d’accès.

```
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```

### <a name="parameters"></a>Paramètres

*pszDir*<br/>
Le chemin du répertoire.

*pszFile*<br/>
Le chemin d’accès du fichier.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathCombine](/windows/desktop/api/shlwapi/nf-shlwapi-pathcombinea).

##  <a name="commonprefix"></a>  CPathT::CommonPrefix

Appelez cette méthode pour déterminer si le chemin d’accès spécifié partage un préfixe commun avec le chemin d’accès actuel.

```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```

### <a name="parameters"></a>Paramètres

*pszOther*<br/>
Le chemin d’accès à comparer à l’objet actuel.

### <a name="return-value"></a>Valeur de retour

Retourne le préfixe commun.

### <a name="remarks"></a>Notes

Un préfixe est un de ces types : « C:\\\\«, ». «, ».. «, ».. \\\\". Pour plus d’informations, consultez [PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa).

##  <a name="compactpath"></a>  CPathT::CompactPath

Appelez cette méthode pour tronquer un chemin d’accès de fichier d’ajuster au sein d’une largeur en pixels donné en remplacement des composants de chemin d’accès avec les points de suspension.

```
BOOL CompactPath(HDC hDC, UINT nWidth);
```

### <a name="parameters"></a>Paramètres

*hDC*<br/>
Le contexte de périphérique utilisé pour la métrique des polices.

*nWidth*<br/>
La largeur, en pixels, qui doit se tenir dans la chaîne.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha).

##  <a name="compactpathex"></a>  CPathT::CompactPathEx

Appelez cette méthode pour tronquer un chemin d’accès de fichier d’ajuster au sein d’un nombre donné de caractères en remplacement des composants de chemin d’accès avec les points de suspension.

```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```

### <a name="parameters"></a>Paramètres

*nMaxChars*<br/>
Le nombre maximal de caractères devant figurer dans la nouvelle chaîne, y compris le caractère NULL de fin.

*dwFlags*<br/>
Réservé.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa).

##  <a name="cpatht"></a>  CPathT::CPathT

Constructeur.

```
CPathT(PCXSTR pszPath);
CPathT(const CPathT<StringType>& path);
CPathT() throw();
```

### <a name="parameters"></a>Paramètres

*pszPath*<br/>
Pointeur vers une chaîne de chemin d’accès.

*path*<br/>
La chaîne de chemin d’accès.

##  <a name="fileexists"></a>  CPathT::FileExists

Appelez cette méthode pour vérifier si le fichier à ce nom de chemin d’accès existe.

```
BOOL FileExists() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le fichier existe, FALSE sinon.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa).

##  <a name="findextension"></a>  CPathT::FindExtension

Appelez cette méthode pour rechercher la position de l’extension de fichier dans le chemin d’accès.

```
int FindExtension() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la position de la «. » précédant l’extension. Si aucune extension n’est trouvée, retourne -1.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona).

##  <a name="findfilename"></a>  CPathT::FindFileName

Appelez cette méthode pour trouver la position du nom de fichier dans le chemin d’accès.

```
int FindFileName() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la position du nom de fichier. Si aucun nom de fichier n’est trouvé, retourne -1.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea).

##  <a name="getdrivenumber"></a>  CPathT::GetDriveNumber

Appelez cette méthode pour rechercher le chemin d’accès pour une lettre de lecteur dans la plage de 'A' à 'Z' et retourner le nombre de lecteur correspondante.

```
int GetDriveNumber() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le nombre de lecteur sous forme d’entier de 0 à 25 (correspondant à « A » à « Z ») si le chemin d’accès comporte une lettre de lecteur, ou -1 dans le cas contraire.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera).

##  <a name="getextension"></a>  CPathT::GetExtension

Appelez cette méthode pour obtenir l’extension de fichier dans le chemin d’accès.

```
StringType GetExtension() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne l’extension de fichier.

##  <a name="isdirectory"></a>  CPathT::IsDirectory

Appelez cette méthode pour vérifier si le chemin d’accès est un répertoire valide.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne une valeur différente de zéro (16) si le chemin d’accès est un répertoire, sinon FALSE.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathIsDirectory](/windows/desktop/api/shlwapi/nf-shlwapi-pathisdirectorya).

##  <a name="isfilespec"></a>  CPathT::IsFileSpec

Appelez cette méthode pour rechercher un chemin d’accès pour tout caractère délimiteur de chemin d’accès (par exemple, ' :' ou '\\'). S’il n’y a aucun caractère délimiteur de chemin d’accès est présent, le chemin d’accès est considéré comme un chemin d’accès de la spécification de fichier.

```
BOOL IsFileSpec() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne TRUE si aucun caractère délimiteur de chemin d’accès dans le chemin d’accès, ou FALSE s’il existe des caractères de délimitation de chemin d’accès.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca).

##  <a name="isprefix"></a>  CPathT::IsPrefix

Appelez cette méthode pour déterminer si un chemin d’accès contient un préfixe valide du type passé *pszPrefix*.

```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```

### <a name="parameters"></a>Paramètres

*pszPrefix*<br/>
Le préfixe à rechercher. Un préfixe est un de ces types : « C:\\\\«, ». «, ».. «, ».. \\\\".

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le chemin d’accès contient le préfixe, ou FALSE dans le cas contraire.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa).

##  <a name="isrelative"></a>  CPathT::IsRelative

Appelez cette méthode pour déterminer si le chemin d’accès est relatif.

```
BOOL IsRelative() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le chemin d’accès est relatif, ou FALSE si elle est absolue.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea).

##  <a name="isroot"></a>  CPathT::IsRoot

Appelez cette méthode pour déterminer si le chemin d’accès est un répertoire racine.

```
BOOL IsRoot() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le chemin d’accès est une racine, ou FALSE dans le cas contraire.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota).

##  <a name="issameroot"></a>  CPathT::IsSameRoot

Appelez cette méthode pour déterminer si un autre chemin d’accès est un composant racine commun avec le chemin d’accès actuel.

```
BOOL IsSameRoot(PCXSTR pszOther) const;
```

### <a name="parameters"></a>Paramètres

*pszOther*<br/>
L’autre tracé.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si les deux chaînes ont le même composant racine, ou FALSE dans le cas contraire.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota).

##  <a name="isunc"></a>  CPathT::IsUNC

Appelez cette méthode pour déterminer si le chemin d’accès est un chemin d’accès UNC (convention universelle d’affectation de noms) valide pour un serveur et le partager.

```
BOOL IsUNC() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le chemin d’accès est un chemin UNC valide, ou FALSE dans le cas contraire.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca).

##  <a name="isuncserver"></a>  CPathT::IsUNCServer

Appelez cette méthode pour déterminer si le chemin d’accès est un chemin d’accès UNC (convention universelle d’affectation de noms) valide pour un seul serveur.

```
BOOL IsUNCServer() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si la chaîne est un chemin d’accès UNC d’un serveur uniquement (aucun nom de partage) valide, ou FALSE.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera).

##  <a name="isuncservershare"></a>  CPathT::IsUNCServerShare

Appelez cette méthode pour déterminer si le chemin d’accès est un chemin de partage UNC (convention universelle d’affectation de noms) valid, \\ \  *server*\ *partager*.

```
BOOL IsUNCServerShare() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le chemin d’accès se présente sous la forme \\ \  *server*\ *partager*, ou FALSE dans le cas contraire.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea).

##  <a name="m_strpath"></a>  CPathT::m_strPath

Chemin d’accès.

```
StringType m_strPath;
```

### <a name="remarks"></a>Notes

`StringType` est le paramètre de modèle à `CPathT`.

##  <a name="makepretty"></a>  CPathT::MakePretty

Appelez cette méthode pour convertir un chemin d’accès à tous les caractères minuscules pour donner le chemin d’accès une apparence cohérente.

```
BOOL MakePretty();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le chemin d’accès a été converti, ou FALSE dans le cas contraire.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya).

##  <a name="matchspec"></a>  CPathT::MatchSpec

Appelez cette méthode pour rechercher le chemin d’accès d’une chaîne contenant un type de correspondance de caractère générique.

```
BOOL MatchSpec(PCXSTR pszSpec) const;
```

### <a name="parameters"></a>Paramètres

*pszSpec*<br/>
Pointeur vers une chaîne se terminant par null avec le type de fichier à rechercher. Par exemple, pour tester si le fichier sur le chemin d’accès actuel est un fichier DOC, *pszSpec* doit être défini sur « * .doc ».

### <a name="return-value"></a>Valeur de retour

Retourne si la chaîne correspond à la valeur TRUE ou FALSE dans le cas contraire.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca).

##  <a name="operator_add_eq"></a>  CPathT::operator +=

Cet opérateur ajoute une chaîne pour le chemin d’accès.

```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```

### <a name="parameters"></a>Paramètres

*pszMore*<br/>
Chaîne à ajouter.

### <a name="return-value"></a>Valeur de retour

Retourne le chemin d’accès de mise à jour.

##  <a name="operator_const_stringtype_amp"></a>  CPathT::operator const StringType &amp;

Cet opérateur permet à l’objet à être traitée comme une chaîne.

```
operator const StringType&() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une chaîne représentant le chemin d’accès actuel géré par cet objet.

##  <a name="operator_cpatht__pcxstr"></a>  CPathT::operator CPathT::PCXSTR

Cet opérateur permet à l’objet à être traitée comme une chaîne.

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une chaîne représentant le chemin d’accès actuel géré par cet objet.

##  <a name="operator_stringtype_amp"></a>  CPathT::operator StringType &amp;

Cet opérateur permet à l’objet à être traitée comme une chaîne.

```
operator StringType&() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une chaîne représentant le chemin d’accès actuel géré par cet objet.

##  <a name="pcxstr"></a>  CPathT::PCXSTR

Un type de chaîne constante.

```
typedef StringType::PCXSTR PCXSTR;
```

### <a name="remarks"></a>Notes

`StringType` est le paramètre de modèle à `CPathT`.

##  <a name="pxstr"></a>  CPathT::PXSTR

Un type chaîne.

```
typedef StringType::PXSTR PXSTR;
```

### <a name="remarks"></a>Notes

`StringType` est le paramètre de modèle à `CPathT`.

##  <a name="quotespaces"></a>  CPathT::QuoteSpaces

Appelez cette méthode pour délimiter le chemin d’accès entre guillemets s’il contient des espaces.

```
void QuoteSpaces();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa).

##  <a name="relativepathto"></a>  CPathT::RelativePathTo

Appelez cette méthode pour créer un chemin d’accès relatif d’un fichier ou dossier à un autre.

```
BOOL RelativePathTo(
    PCXSTR pszFrom,
    DWORD dwAttrFrom,
    PCXSTR pszTo,
    DWORD dwAttrTo);
```

### <a name="parameters"></a>Paramètres

*pszFrom*<br/>
Début du chemin d’accès relatif.

*dwAttrFrom*<br/>
Les attributs du fichier de *pszFrom*. Si cette valeur contient FILE_ATTRIBUTE_DIRECTORY, *pszFrom* est censé être un répertoire ; sinon, *pszFrom* est supposé pour être un fichier.

*pszTo*<br/>
Le point de terminaison du chemin d’accès relatif.

*dwAttrTo*<br/>
Les attributs du fichier de *pszTo*. Si cette valeur contient FILE_ATTRIBUTE_DIRECTORY, *pszTo* est censé être un répertoire ; sinon, *pszTo* est supposé pour être un fichier.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa).

##  <a name="removeargs"></a>  CPathT::RemoveArgs

Appelez cette méthode pour supprimer tous les arguments de ligne de commande à partir du chemin.

```
void RemoveArgs();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa).

##  <a name="removebackslash"></a>  CPathT::RemoveBackslash

Appelez cette méthode pour supprimer la barre oblique de fin du chemin d’accès.

```
void RemoveBackslash();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha).

##  <a name="removeblanks"></a>  CPathT::RemoveBlanks

Appelez cette méthode pour supprimer tous les espaces de début et de fin du chemin d’accès.

```
void RemoveBlanks();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa).

##  <a name="removeextension"></a>  CPathT::RemoveExtension

Appelez cette méthode pour supprimer l’extension de fichier du chemin d’accès, le cas échéant.

```
void RemoveExtension();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona).

##  <a name="removefilespec"></a>  CPathT::RemoveFileSpec

Appelez cette méthode pour supprimer le nom de fichier à droite et la barre oblique inverse à partir du chemin, s’il a les.

```
BOOL RemoveFileSpec();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca).

##  <a name="renameextension"></a>  CPathT::RenameExtension

Appelez cette méthode pour remplacer l’extension de nom de fichier dans le chemin d’accès avec une nouvelle extension. Si le nom de fichier ne contient pas une extension, l’extension sera attachée à la fin du chemin d’accès.

```
BOOL RenameExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Paramètres

*pszExtension*<br/>
La nouvelle extension de nom de fichier, précédé par un «. » caractères.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona).

##  <a name="skiproot"></a>  CPathT::SkipRoot

Appelez cette méthode pour analyser un chemin d’accès, en ignorant la lettre de lecteur ou les parties de chemin d’accès UNC (convention universelle d’affectation de noms) / partage de serveur.

```
int SkipRoot() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la position de début du sous-tracé qui suit la racine (lettre de lecteur ou UNC/partage de serveur).

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota).

##  <a name="strippath"></a>  CPathT::StripPath

Appelez cette méthode pour supprimer la partie de chemin d’accès d’un chemin d’accès complet et le nom de fichier.

```
void StripPath();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha).

##  <a name="striptoroot"></a>  CPathT::StripToRoot

Appelez cette méthode pour supprimer toutes les parties du chemin d’accès à l’exception des informations sur les racine.

```
BOOL StripToRoot();
```

### <a name="return-value"></a>Valeur de retour

Retourne TRUE si une lettre de lecteur valide a été trouvé dans le chemin d’accès, ou FALSE dans le cas contraire.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota).

##  <a name="unquotespaces"></a>  CPathT::UnquoteSpaces

Appelez cette méthode pour supprimer les guillemets de début et de fin d’un chemin d’accès.

```
void UnquoteSpaces();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa).

##  <a name="xchar"></a>  CPathT::XCHAR

Type de caractère.

```
typedef StringType::XCHAR XCHAR;
```

### <a name="remarks"></a>Notes

`StringType` est le paramètre de modèle à `CPathT`.

## <a name="see-also"></a>Voir aussi

[Classes](../../atl/reference/atl-classes.md)<br/>
[CStringT, classe](../../atl-mfc-shared/reference/cstringt-class.md)
