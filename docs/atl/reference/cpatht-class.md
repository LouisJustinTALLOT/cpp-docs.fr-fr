---
title: CPathT, classe
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
ms.openlocfilehash: ba1c831d772deef34449d17adc2c8e7a6f90eaef
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "69496619"
---
# <a name="cpatht-class"></a>CPathT, classe

Cette classe représente un chemin d’accès.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <typename StringType>
class CPathT
```

#### <a name="parameters"></a>Paramètres

*StringType*<br/>
Classe de chaîne ATL/MFC à utiliser pour le chemin d’accès (consultez [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)).

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Name|Description|
|----------|-----------------|
|[CPathT::PCXSTR](#pcxstr)|Type chaîne constante.|
|[CPathT::PXSTR](#pxstr)|Type chaîne.|
|[CPathT::XCHAR](#xchar)|Type de caractère.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CPathT::CPathT](#cpatht)|Constructeur pour le chemin d’accès.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPathT::AddBackslash](#addbackslash)|Appelez cette méthode pour ajouter une barre oblique inverse à la fin d’une chaîne afin de créer la syntaxe correcte pour un chemin d’accès.|
|[CPathT::AddExtension](#addextension)|Appelez cette méthode pour ajouter une extension de fichier à un chemin d’accès.|
|[CPathT::Append](#append)|Appelez cette méthode pour ajouter une chaîne au chemin d’accès actuel.|
|[CPathT::BuildRoot](#buildroot)|Appelez cette méthode pour créer un chemin d’accès racine à partir d’un numéro de lecteur donné.|
|[CPathT::Canonicalize](#canonicalize)|Appelez cette méthode pour convertir le chemin d’accès au format canonique.|
|[CPathT::Combine](#combine)|Appelez cette méthode pour concaténer une chaîne représentant un nom de répertoire et une chaîne représentant un nom de chemin d’accès de fichier en un seul chemin d’accès.|
|[CPathT::CommonPrefix](#commonprefix)|Appelez cette méthode pour déterminer si le chemin d’accès spécifié partage un préfixe commun avec le chemin d’accès actuel.|
|[CPathT::CompactPath](#compactpath)|Appelez cette méthode pour tronquer un chemin d’accès de fichier pour l’ajuster à une largeur de pixel donnée en remplaçant des composants de chemin d’accès par des ellipses.|
|[CPathT::CompactPathEx](#compactpathex)|Appelez cette méthode pour tronquer un chemin d’accès de fichier à ajuster au sein d’un nombre donné de caractères en remplaçant les composants du chemin par des ellipses.|
|[CPathT::FileExists](#fileexists)|Appelez cette méthode pour vérifier si le fichier se trouve à ce nom de chemin d’accès.|
|[CPathT::FindExtension](#findextension)|Appelez cette méthode pour rechercher la position de l’extension de fichier dans le chemin d’accès.|
|[CPathT::FindFileName](#findfilename)|Appelez cette méthode pour rechercher la position du nom de fichier dans le chemin d’accès.|
|[CPathT::GetDriveNumber](#getdrivenumber)|Appelez cette méthode pour rechercher dans le chemin d’accès une lettre de lecteur comprise entre « A » et « Z » et retourner le numéro de lecteur correspondant.|
|[CPathT::GetExtension](#getextension)|Appelez cette méthode pour récupérer l’extension de fichier à partir du chemin d’accès.|
|[CPathT::IsDirectory](#isdirectory)|Appelez cette méthode pour vérifier si le chemin d’accès est un répertoire valide.|
|[CPathT::IsFileSpec](#isfilespec)|Appelez cette méthode pour rechercher un chemin d’accès pour les caractères délimitant les chemins d’accès (par exemple, '\\: 'ou' '). Si aucun caractère de délimitation de chemin d’accès n’est présent, le chemin d’accès est considéré comme un chemin d’accès de spécifications de fichier.|
|[CPathT::IsPrefix](#isprefix)|Appelez cette méthode pour déterminer si un chemin d’accès contient un préfixe valide du type passé par *pszPrefix*.|
|[CPathT::IsRelative](#isrelative)|Appelez cette méthode pour déterminer si le chemin d’accès est relatif.|
|[CPathT::IsRoot](#isroot)|Appelez cette méthode pour déterminer si le chemin d’accès est une racine de répertoire.|
|[CPathT::IsSameRoot](#issameroot)|Appelez cette méthode pour déterminer si un autre chemin d’accès a un composant racine commun avec le chemin d’accès actuel.|
|[CPathT::IsUNC](#isunc)|Appelez cette méthode pour déterminer si le chemin d’accès est un chemin d’accès UNC (Universal Naming Convention) valide pour un serveur et un partage.|
|[CPathT::IsUNCServer](#isuncserver)|Appelez cette méthode pour déterminer si le chemin d’accès est un chemin d’accès UNC (Universal Naming Convention) valide pour un serveur uniquement.|
|[CPathT::IsUNCServerShare](#isuncservershare)|Appelez cette méthode pour déterminer si le chemin d’accès est un chemin de partage UNC (Universal Naming Convention \\) valide, \ le*partage*de *serveur*\ .|
|[CPathT::MakePretty](#makepretty)|Appelez cette méthode pour convertir un chemin d’accès en caractères minuscules pour que le chemin d’accès soit une apparence cohérente.|
|[CPathT::MatchSpec](#matchspec)|Appelez cette méthode pour rechercher dans le chemin d’accès une chaîne contenant un type de correspondance de caractère générique.|
|[CPathT::QuoteSpaces](#quotespaces)|Appelez cette méthode pour placer le chemin d’accès entre guillemets s’il contient des espaces.|
|[CPathT::RelativePathTo](#relativepathto)|Appelez cette méthode pour créer un chemin d’accès relatif d’un fichier ou dossier à un autre.|
|[CPathT::RemoveArgs](#removeargs)|Appelez cette méthode pour supprimer tous les arguments de ligne de commande du chemin d’accès.|
|[CPathT::RemoveBackslash](#removebackslash)|Appelez cette méthode pour supprimer la barre oblique inverse à la fin du chemin d’accès.|
|[CPathT::RemoveBlanks](#removeblanks)|Appelez cette méthode pour supprimer tous les espaces de début et de fin du chemin d’accès.|
|[CPathT::RemoveExtension](#removeextension)|Appelez cette méthode pour supprimer l’extension de fichier du chemin d’accès, le cas échéant.|
|[CPathT::RemoveFileSpec](#removefilespec)|Appelez cette méthode pour supprimer le nom du fichier de fin et la barre oblique inverse du chemin d’accès, s’il en possède.|
|[CPathT::RenameExtension](#renameextension)|Appelez cette méthode pour remplacer l’extension de nom de fichier dans le chemin d’accès par une nouvelle extension. Si le nom de fichier ne contient pas d’extension, l’extension est attachée à la fin de la chaîne.|
|[CPathT::SkipRoot](#skiproot)|Appelez cette méthode pour analyser un chemin d’accès, en ignorant la lettre de lecteur ou le serveur UNC/les parties du chemin d’accès de partage.|
|[CPathT::StripPath](#strippath)|Appelez cette méthode pour supprimer la partie du chemin d’accès qualifié complet et le nom de fichier.|
|[CPathT::StripToRoot](#striptoroot)|Appelez cette méthode pour supprimer toutes les parties du chemin d’accès, à l’exception des informations de racine.|
|[CPathT::UnquoteSpaces](#unquotespaces)|Appelez cette méthode pour supprimer les guillemets à partir du début et de la fin d’un chemin d’accès.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CPathT :: Operator const StringType &](#operator_const_stringtype_amp)|Cet opérateur permet à l’objet d’être traité comme une chaîne.|
|[CPathT :: Operator CPathT ::P CXSTR](#operator_cpatht__pcxstr)|Cet opérateur permet à l’objet d’être traité comme une chaîne.|
|[CPathT :: Operator StringType &](#operator_stringtype_amp)|Cet opérateur permet à l’objet d’être traité comme une chaîne.|
|[CPathT::operator +=](#operator_add_eq)|Cet opérateur ajoute une chaîne au chemin d’accès.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPathT::m_strPath](#m_strpath)|Chemin d’accès.|

## <a name="remarks"></a>Notes

`CPath`, `CPathA` `CPathT` et `CPathW` sont des instanciations de définies comme suit :

`typedef CPathT< CString > CPath;`

`typedef CPathT< CStringA > CPathA;`

`typedef CPathT< CStringW > CPathW;`

## <a name="requirements"></a>Configuration requise

**En-tête :** atlpath. h

##  <a name="addbackslash"></a>  CPathT::AddBackslash

Appelez cette méthode pour ajouter une barre oblique inverse à la fin d’une chaîne afin de créer la syntaxe correcte pour un chemin d’accès. Si le chemin d’accès contient déjà une barre oblique inverse de fin, aucune barre oblique inverse n’est ajoutée.

```
void AddBackslash();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathAddBackSlash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).

##  <a name="addextension"></a>  CPathT::AddExtension

Appelez cette méthode pour ajouter une extension de fichier à un chemin d’accès.

```
BOOL AddExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Paramètres

*pszExtension*<br/>
Extension de fichier à ajouter.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).

##  <a name="append"></a>  CPathT::Append

Appelez cette méthode pour ajouter une chaîne au chemin d’accès actuel.

```
BOOL Append(PCXSTR pszMore);
```

### <a name="parameters"></a>Paramètres

*pszMore*<br/>
Chaîne à ajouter.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).

##  <a name="buildroot"></a>  CPathT::BuildRoot

Appelez cette méthode pour créer un chemin d’accès racine à partir d’un numéro de lecteur donné.

```
void BuildRoot(int iDrive);
```

### <a name="parameters"></a>Paramètres

*iDrive*<br/>
Le numéro de lecteur (0 est un :, 1 est B :, etc.).

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).

##  <a name="canonicalize"></a>  CPathT::Canonicalize

Appelez cette méthode pour convertir le chemin d’accès au format canonique.

```
void Canonicalize();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).

##  <a name="combine"></a>  CPathT::Combine

Appelez cette méthode pour concaténer une chaîne représentant un nom de répertoire et une chaîne représentant un nom de chemin d’accès de fichier en un seul chemin d’accès.

```
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```

### <a name="parameters"></a>Paramètres

*pszDir*<br/>
Chemin d’accès au répertoire.

*pszFile*<br/>
Chemin d’accès du fichier.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).

##  <a name="commonprefix"></a>  CPathT::CommonPrefix

Appelez cette méthode pour déterminer si le chemin d’accès spécifié partage un préfixe commun avec le chemin d’accès actuel.

```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```

### <a name="parameters"></a>Paramètres

*pszOther*<br/>
Chemin d’accès à comparer à l’objet actuel.

### <a name="return-value"></a>Valeur de retour

Retourne le préfixe commun.

### <a name="remarks"></a>Notes

Un préfixe est l’un des types suivants : "C :\\\\", ".", "..", ".. \\\\". Pour plus d’informations, consultez [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).

##  <a name="compactpath"></a>  CPathT::CompactPath

Appelez cette méthode pour tronquer un chemin d’accès de fichier pour l’ajuster à une largeur de pixel donnée en remplaçant des composants de chemin d’accès par des ellipses.

```
BOOL CompactPath(HDC hDC, UINT nWidth);
```

### <a name="parameters"></a>Paramètres

*hDC*<br/>
Contexte de périphérique (Device Context) utilisé pour les métriques de police.

*nWidth*<br/>
Largeur, en pixels, à laquelle la chaîne doit s’ajuster.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).

##  <a name="compactpathex"></a>  CPathT::CompactPathEx

Appelez cette méthode pour tronquer un chemin d’accès de fichier à ajuster au sein d’un nombre donné de caractères en remplaçant les composants du chemin par des ellipses.

```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```

### <a name="parameters"></a>Paramètres

*nMaxChars*<br/>
Nombre maximal de caractères à inclure dans la nouvelle chaîne, y compris le caractère NULL de fin.

*dwFlags*<br/>
Réservé.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).

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
Chaîne du chemin d’accès.

##  <a name="fileexists"></a>  CPathT::FileExists

Appelez cette méthode pour vérifier si le fichier se trouve à ce nom de chemin d’accès.

```
BOOL FileExists() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le fichier existe ; sinon, FALSe.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).

##  <a name="findextension"></a>  CPathT::FindExtension

Appelez cette méthode pour rechercher la position de l’extension de fichier dans le chemin d’accès.

```
int FindExtension() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la position du « . » précédant l’extension. Si aucune extension n’est trouvée, retourne-1.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).

##  <a name="findfilename"></a>  CPathT::FindFileName

Appelez cette méthode pour rechercher la position du nom de fichier dans le chemin d’accès.

```
int FindFileName() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la position du nom de fichier. Si aucun nom de fichier n’est trouvé, retourne-1.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).

##  <a name="getdrivenumber"></a>  CPathT::GetDriveNumber

Appelez cette méthode pour rechercher dans le chemin d’accès une lettre de lecteur comprise entre « A » et « Z » et retourner le numéro de lecteur correspondant.

```
int GetDriveNumber() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le numéro de lecteur sous la forme d’un entier compris entre 0 et 25 (correspondant à « A » à « Z ») si le chemin d’accès a une lettre de lecteur, ou-1 dans le cas contraire.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).

##  <a name="getextension"></a>  CPathT::GetExtension

Appelez cette méthode pour récupérer l’extension de fichier à partir du chemin d’accès.

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

Retourne une valeur différente de zéro (16) si le chemin d’accès est un répertoire ; sinon, FALSe.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).

##  <a name="isfilespec"></a>  CPathT::IsFileSpec

Appelez cette méthode pour rechercher un chemin d’accès pour les caractères délimitant les chemins d’accès (par exemple, '\\: 'ou' '). Si aucun caractère de délimitation de chemin d’accès n’est présent, le chemin d’accès est considéré comme un chemin d’accès de spécifications de fichier.

```
BOOL IsFileSpec() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE s’il n’y a pas de caractères de délimitation du chemin d’accès dans le chemin d’accès, ou FALSe s’il existe des caractères de délimitation de chemin d’accès.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).

##  <a name="isprefix"></a>  CPathT::IsPrefix

Appelez cette méthode pour déterminer si un chemin d’accès contient un préfixe valide du type passé par *pszPrefix*.

```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```

### <a name="parameters"></a>Paramètres

*pszPrefix*<br/>
Préfixe à rechercher. Un préfixe est l’un des types suivants : "C :\\\\", ".", "..", ".. \\\\".

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le chemin d’accès contient le préfixe, ou FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw).

##  <a name="isrelative"></a>  CPathT::IsRelative

Appelez cette méthode pour déterminer si le chemin d’accès est relatif.

```
BOOL IsRelative() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le chemin d’accès est relatif, ou FALSe s’il est absolu.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).

##  <a name="isroot"></a>  CPathT::IsRoot

Appelez cette méthode pour déterminer si le chemin d’accès est une racine de répertoire.

```
BOOL IsRoot() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le chemin d’accès est une racine, ou FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).

##  <a name="issameroot"></a>  CPathT::IsSameRoot

Appelez cette méthode pour déterminer si un autre chemin d’accès a un composant racine commun avec le chemin d’accès actuel.

```
BOOL IsSameRoot(PCXSTR pszOther) const;
```

### <a name="parameters"></a>Paramètres

*pszOther*<br/>
Autre chemin d’accès.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si les deux chaînes ont le même composant racine, ou FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw).

##  <a name="isunc"></a>  CPathT::IsUNC

Appelez cette méthode pour déterminer si le chemin d’accès est un chemin d’accès UNC (Universal Naming Convention) valide pour un serveur et un partage.

```
BOOL IsUNC() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le chemin d’accès est un chemin d’accès UNC valide, ou FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).

##  <a name="isuncserver"></a>  CPathT::IsUNCServer

Appelez cette méthode pour déterminer si le chemin d’accès est un chemin d’accès UNC (Universal Naming Convention) valide pour un serveur uniquement.

```
BOOL IsUNCServer() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si la chaîne est un chemin d’accès UNC valide pour un serveur uniquement (pas de nom de partage), ou FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).

##  <a name="isuncservershare"></a>  CPathT::IsUNCServerShare

Appelez cette méthode pour déterminer si le chemin d’accès est un chemin de partage UNC (Universal Naming Convention \\) valide, \ le*partage*de *serveur*\ .

```
BOOL IsUNCServerShare() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur true si le chemin d’accès \\est \ au format *Server*\ *share*, ou false dans le cas contraire.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).

##  <a name="m_strpath"></a>  CPathT::m_strPath

Chemin d’accès.

```
StringType m_strPath;
```

### <a name="remarks"></a>Notes

`StringType`est le paramètre de modèle `CPathT`de.

##  <a name="makepretty"></a>  CPathT::MakePretty

Appelez cette méthode pour convertir un chemin d’accès en caractères minuscules pour que le chemin d’accès soit une apparence cohérente.

```
BOOL MakePretty();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si le chemin d’accès a été converti, ou FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).

##  <a name="matchspec"></a>  CPathT::MatchSpec

Appelez cette méthode pour rechercher dans le chemin d’accès une chaîne contenant un type de correspondance de caractère générique.

```
BOOL MatchSpec(PCXSTR pszSpec) const;
```

### <a name="parameters"></a>Paramètres

*pszSpec*<br/>
Pointeur vers une chaîne se terminant par un caractère NULL avec le type de fichier à rechercher. Par exemple, pour tester si le fichier situé dans le chemin d’accès actuel est un fichier DOC, *pszSpec* doit être défini sur « *. doc ».

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si la chaîne correspond, ou FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).

##  <a name="operator_add_eq"></a>  CPathT::operator +=

Cet opérateur ajoute une chaîne au chemin d’accès.

```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```

### <a name="parameters"></a>Paramètres

*pszMore*<br/>
Chaîne à ajouter.

### <a name="return-value"></a>Valeur de retour

Retourne le chemin d’accès mis à jour.

##  <a name="operator_const_stringtype_amp"></a>CPathT :: Operator const StringType&amp;

Cet opérateur permet à l’objet d’être traité comme une chaîne.

```
operator const StringType&() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une chaîne représentant le chemin d’accès actuel managé par cet objet.

##  <a name="operator_cpatht__pcxstr"></a>CPathT :: Operator CPathT ::P CXSTR

Cet opérateur permet à l’objet d’être traité comme une chaîne.

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une chaîne représentant le chemin d’accès actuel managé par cet objet.

##  <a name="operator_stringtype_amp"></a>CPathT :: Operator StringType&amp;

Cet opérateur permet à l’objet d’être traité comme une chaîne.

```
operator StringType&() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une chaîne représentant le chemin d’accès actuel managé par cet objet.

##  <a name="pcxstr"></a>  CPathT::PCXSTR

Type chaîne constante.

```
typedef StringType::PCXSTR PCXSTR;
```

### <a name="remarks"></a>Notes

`StringType`est le paramètre de modèle `CPathT`de.

##  <a name="pxstr"></a>  CPathT::PXSTR

Type chaîne.

```
typedef StringType::PXSTR PXSTR;
```

### <a name="remarks"></a>Notes

`StringType`est le paramètre de modèle `CPathT`de.

##  <a name="quotespaces"></a>  CPathT::QuoteSpaces

Appelez cette méthode pour placer le chemin d’accès entre guillemets s’il contient des espaces.

```
void QuoteSpaces();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).

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
Attributs de fichier de *pszFrom*. Si cette valeur contient FILE_ATTRIBUTE_DIRECTORY, *pszFrom* est supposé être un répertoire ; dans le cas contraire, *pszFrom* est supposé être un fichier.

*pszTo*<br/>
Point de terminaison du chemin d’accès relatif.

*dwAttrTo*<br/>
Attributs de fichier de *pszTo*. Si cette valeur contient FILE_ATTRIBUTE_DIRECTORY, *pszTo* est supposé être un répertoire ; dans le cas contraire, *pszTo* est supposé être un fichier.

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).

##  <a name="removeargs"></a>  CPathT::RemoveArgs

Appelez cette méthode pour supprimer tous les arguments de ligne de commande du chemin d’accès.

```
void RemoveArgs();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).

##  <a name="removebackslash"></a>  CPathT::RemoveBackslash

Appelez cette méthode pour supprimer la barre oblique inverse à la fin du chemin d’accès.

```
void RemoveBackslash();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).

##  <a name="removeblanks"></a>  CPathT::RemoveBlanks

Appelez cette méthode pour supprimer tous les espaces de début et de fin du chemin d’accès.

```
void RemoveBlanks();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).

##  <a name="removeextension"></a>  CPathT::RemoveExtension

Appelez cette méthode pour supprimer l’extension de fichier du chemin d’accès, le cas échéant.

```
void RemoveExtension();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).

##  <a name="removefilespec"></a>  CPathT::RemoveFileSpec

Appelez cette méthode pour supprimer le nom du fichier de fin et la barre oblique inverse du chemin d’accès, s’il en possède.

```
BOOL RemoveFileSpec();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).

##  <a name="renameextension"></a>  CPathT::RenameExtension

Appelez cette méthode pour remplacer l’extension de nom de fichier dans le chemin d’accès par une nouvelle extension. Si le nom de fichier ne contient pas d’extension, l’extension est attachée à la fin du chemin d’accès.

```
BOOL RenameExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Paramètres

*pszExtension*<br/>
Nouvelle extension de nom de fichier, précédée d’un caractère « . ».

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE en cas de réussite, FALSe en cas d’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).

##  <a name="skiproot"></a>  CPathT::SkipRoot

Appelez cette méthode pour analyser un chemin d’accès, en ignorant la lettre de lecteur ou les parties du chemin d’accès du serveur/partage UNC (Universal Naming Convention).

```
int SkipRoot() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la position du début du sous-chemin d’accès qui suit la racine (lettre de lecteur ou serveur/partage UNC).

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).

##  <a name="strippath"></a>  CPathT::StripPath

Appelez cette méthode pour supprimer la partie du chemin d’accès qualifié complet et le nom de fichier.

```
void StripPath();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).

##  <a name="striptoroot"></a>  CPathT::StripToRoot

Appelez cette méthode pour supprimer toutes les parties du chemin d’accès, à l’exception des informations de racine.

```
BOOL StripToRoot();
```

### <a name="return-value"></a>Valeur de retour

Retourne la valeur TRUE si une lettre de lecteur valide a été trouvée dans le chemin d’accès, ou FALSe dans le cas contraire.

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).

##  <a name="unquotespaces"></a>  CPathT::UnquoteSpaces

Appelez cette méthode pour supprimer les guillemets à partir du début et de la fin d’un chemin d’accès.

```
void UnquoteSpaces();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).

##  <a name="xchar"></a>  CPathT::XCHAR

Type de caractère.

```
typedef StringType::XCHAR XCHAR;
```

### <a name="remarks"></a>Notes

`StringType`est le paramètre de modèle `CPathT`de.

## <a name="see-also"></a>Voir aussi

[Classes](../../atl/reference/atl-classes.md)<br/>
[CStringT, classe](../../atl-mfc-shared/reference/cstringt-class.md)
