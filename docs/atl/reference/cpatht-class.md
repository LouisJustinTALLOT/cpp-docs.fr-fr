---
title: Classe CPathT
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
ms.openlocfilehash: 76273e7fbfa50e610b437e11859821374413d008
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032132"
---
# <a name="cpatht-class"></a>Classe CPathT

Cette classe représente un chemin.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <typename StringType>
class CPathT
```

#### <a name="parameters"></a>Paramètres

*StringType*<br/>
La classe de cordes ATL/MFC à utiliser pour le chemin (voir [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)).

## <a name="members"></a>Membres

### <a name="public-typedefs"></a>Typedefs publics

|Nom|Description|
|----------|-----------------|
|[CPathT::PCXSTR](#pcxstr)|Un type de chaîne constant.|
|[CPathT::PXSTR](#pxstr)|Type chaîne.|
|[CPathT::XCHAR](#xchar)|Type de caractère.|

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CPathT::CPathT](#cpatht)|Le constructeur pour le chemin.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CPathT::AddBackslash](#addbackslash)|Appelez cette méthode pour ajouter un contredage à l’extrémité d’une chaîne pour créer la syntaxe correcte pour un chemin.|
|[CPathT::AddExtension](#addextension)|Appelez cette méthode pour ajouter une extension de fichier à un chemin.|
|[CPathT::Append](#append)|Appelez cette méthode pour ajouter une corde au chemin actuel.|
|[CPathT::BuildRoot](#buildroot)|Appelez cette méthode pour créer un chemin de racine à partir d’un numéro d’entraînement donné.|
|[CPathT::Canonicalize](#canonicalize)|Appelez cette méthode pour convertir le chemin en forme canonique.|
|[CPathT::Combinez](#combine)|Appelez cette méthode pour concatenate une chaîne représentant un nom d’annuaire et une chaîne représentant un nom de chemin de fichier dans un chemin.|
|[CPathT::CommonPrefix](#commonprefix)|Appelez cette méthode pour déterminer si le chemin spécifié partage un préfixe commun avec le chemin actuel.|
|[CPathT::CompactPath](#compactpath)|Appelez cette méthode pour tronquer un chemin de fichier pour s’adapter dans une largeur de pixel donnée en remplaçant les composants du chemin par l’ellipsis.|
|[CPathT::CompactPathEx](#compactpathex)|Appelez cette méthode pour tronquer un chemin de fichier pour s’adapter à un nombre donné de caractères en remplaçant les composants du chemin par l’ellipsis.|
|[CPathT::FileExists](#fileexists)|Appelez cette méthode pour vérifier si le fichier à ce nom de chemin existe.|
|[CPathT::FindExtension](#findextension)|Appelez cette méthode pour trouver la position de l’extension du fichier dans le chemin.|
|[CPathT::FindFileName](#findfilename)|Appelez cette méthode pour trouver la position du nom du fichier dans le chemin.|
|[CPathT::GetDriveNumber](#getdrivenumber)|Appelez cette méthode pour rechercher le chemin à la recherche d’une lettre d’entraînement dans la plage de 'A' à 'Z' et retourner le numéro d’entraînement correspondant.|
|[CPathT:GetExtension](#getextension)|Appelez cette méthode pour obtenir l’extension du fichier à partir du chemin.|
|[CPathT::IsDirectory](#isdirectory)|Appelez cette méthode pour vérifier si le chemin est un répertoire valide.|
|[CPathT::IsFileSpec](#isfilespec)|Appelez cette méthode pour rechercher un chemin pour tous les personnages délimiter\\le chemin (par exemple, «:» ou '). S’il n’y a pas de personnages délimiter les chemins présents, le chemin est considéré comme un chemin De file Spec.|
|[CPathT::IsPrefix](#isprefix)|Appelez cette méthode pour déterminer si un chemin contient un préfixe valide du type passé par *pszPrefix*.|
|[CPathT:IsRelative](#isrelative)|Appelez cette méthode pour déterminer si le chemin est relatif.|
|[CPathT::IsRoot](#isroot)|Appelez cette méthode pour déterminer si le chemin est une racine d’annuaire.|
|[CPathT::IsSameRoot](#issameroot)|Appelez cette méthode pour déterminer si un autre chemin a une composante racine commune avec le chemin actuel.|
|[CPathT:IsUNC](#isunc)|Appelez cette méthode pour déterminer si le chemin est un chemin valide UNC (convention universelle de nommage) pour un serveur et partager.|
|[CPathT:IsUNCServer](#isuncserver)|Appelez cette méthode pour déterminer si le chemin est un chemin valide UNC (convention universelle de nommage) pour un serveur seulement.|
|[CPathT::IsUNCServerShare](#isuncservershare)|Appelez cette méthode pour déterminer si le chemin est un moyen \\ \ valide UNC (convention universelle de nommage) partager chemin,*partage* *de serveur*\ .|
|[CPathT::MakePretty](#makepretty)|Appelez cette méthode pour convertir un chemin à tous les caractères minuscules pour donner au chemin une apparence cohérente.|
|[CPathT::MatchSpec](#matchspec)|Appelez cette méthode pour rechercher le chemin pour une chaîne contenant un type de match wildcard.|
|[CPathT::QuoteSpaces](#quotespaces)|Appelez cette méthode pour enfermer le chemin dans des guillemets s’il contient des espaces.|
|[CPathT::RelativePathTo](#relativepathto)|Appelez cette méthode pour créer un chemin relatif d’un fichier ou d’un dossier à un autre.|
|[CPathT::SupprimerArgs](#removeargs)|Appelez cette méthode pour supprimer tous les arguments de ligne de commande du chemin.|
|[CPathT::RemoveBackslash](#removebackslash)|Appelez cette méthode pour enlever la barre oblique arrière de fuite du chemin.|
|[CPathT::RemoveBlanks](#removeblanks)|Appelez cette méthode pour enlever tous les espaces de tête et de fuite du chemin.|
|[CPathT::Supprimerextension](#removeextension)|Appelez cette méthode pour supprimer l’extension du fichier du chemin, s’il y en a une.|
|[CPathT::RemoveFileSpec](#removefilespec)|Appelez cette méthode pour supprimer le nom de fichier de fuite et la barre oblique inverse du chemin, si elle les a.|
|[CPathT::RenameExtension](#renameextension)|Appelez cette méthode pour remplacer l’extension du nom de fichier dans le chemin par une nouvelle extension. Si le nom du fichier ne contient pas d’extension, l’extension sera fixée à l’extrémité de la chaîne.|
|[CPathT::SkipRoot](#skiproot)|Appelez cette méthode pour analyser un chemin, en ignorant la lettre d’entraînement ou le serveur DE l’UNC / partager les parties de chemin.|
|[CPathT::StripPath](#strippath)|Appelez cette méthode pour supprimer la partie de chemin d’un chemin entièrement qualifié et le nom de fichier.|
|[CPathT::StripToRoot](#striptoroot)|Appelez cette méthode pour supprimer toutes les parties du chemin, sauf pour les informations de racine.|
|[CPathT::UnquoteSpaces](#unquotespaces)|Appelez cette méthode pour supprimer les guillemets du début et de la fin d’un chemin.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CPathT::opérateur const StringType &](#operator_const_stringtype_amp)|Cet opérateur permet de traiter l’objet comme une chaîne.|
|[CPathT::opérateur CPathT::PCXSTR](#operator_cpatht__pcxstr)|Cet opérateur permet de traiter l’objet comme une chaîne.|
|[CPathT::opérateur StringType &](#operator_stringtype_amp)|Cet opérateur permet de traiter l’objet comme une chaîne.|
|[CPathT::opérateur](#operator_add_eq)|Cet opérateur attache une corde au chemin.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CPathT::m_strPath](#m_strpath)|Le chemin d'accès.|

## <a name="remarks"></a>Notes

`CPath`, `CPathA`et `CPathW` sont des instantanés de `CPathT` défini comme suit:

`typedef CPathT< CString > CPath;`

`typedef CPathT< CStringA > CPathA;`

`typedef CPathT< CStringW > CPathW;`

## <a name="requirements"></a>Spécifications

**En-tête:** atlpath.h

## <a name="cpathtaddbackslash"></a><a name="addbackslash"></a>CPathT::AddBackslash

Appelez cette méthode pour ajouter un contredage à l’extrémité d’une chaîne pour créer la syntaxe correcte pour un chemin. Si le chemin a déjà une barre oblique arrière de fuite, aucune barre oblique inverse ne sera ajoutée.

```cpp
void AddBackslash();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathAddBackSlash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).

## <a name="cpathtaddextension"></a><a name="addextension"></a>CPathT::AddExtension

Appelez cette méthode pour ajouter une extension de fichier à un chemin.

```
BOOL AddExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Paramètres

*pszExtension*<br/>
L’extension de fichier à ajouter.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).

## <a name="cpathtappend"></a><a name="append"></a>CPathT::Append

Appelez cette méthode pour ajouter une corde au chemin actuel.

```
BOOL Append(PCXSTR pszMore);
```

### <a name="parameters"></a>Paramètres

*pszMore*<br/>
Chaîne à ajouter.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).

## <a name="cpathtbuildroot"></a><a name="buildroot"></a>CPathT::BuildRoot

Appelez cette méthode pour créer un chemin de racine à partir d’un numéro d’entraînement donné.

```cpp
void BuildRoot(int iDrive);
```

### <a name="parameters"></a>Paramètres

*Idrive*<br/>
Le numéro d’entraînement (0 est A:, 1 est B:, et ainsi de suite).

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).

## <a name="cpathtcanonicalize"></a><a name="canonicalize"></a>CPathT::Canonicalize

Appelez cette méthode pour convertir le chemin en forme canonique.

```cpp
void Canonicalize();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).

## <a name="cpathtcombine"></a><a name="combine"></a>CPathT::Combinez

Appelez cette méthode pour concatenate une chaîne représentant un nom d’annuaire et une chaîne représentant un nom de chemin de fichier dans un chemin.

```cpp
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```

### <a name="parameters"></a>Paramètres

*pszDir*<br/>
Chemin d'accès du répertoire.

*pszFile*<br/>
Chemin d'accès du fichier.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).

## <a name="cpathtcommonprefix"></a><a name="commonprefix"></a>CPathT::CommonPrefix

Appelez cette méthode pour déterminer si le chemin spécifié partage un préfixe commun avec le chemin actuel.

```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```

### <a name="parameters"></a>Paramètres

*pszOther*<br/>
Le chemin à comparer à l’actuel.

### <a name="return-value"></a>Valeur de retour

Retourne le préfixe commun.

### <a name="remarks"></a>Notes

Un préfixe est l’un\\\\de ces types: "C: ", ".", "..", ".. \\\\". Pour plus d’informations, voir [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).

## <a name="cpathtcompactpath"></a><a name="compactpath"></a>CPathT::CompactPath

Appelez cette méthode pour tronquer un chemin de fichier pour s’adapter dans une largeur de pixel donnée en remplaçant les composants du chemin par l’ellipsis.

```
BOOL CompactPath(HDC hDC, UINT nWidth);
```

### <a name="parameters"></a>Paramètres

*Hdc*<br/>
Le contexte de l’appareil utilisé pour les mesures de police.

*nWidth (en)*<br/>
La largeur, en pixels, que la chaîne sera obligée de s’intégrer.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).

## <a name="cpathtcompactpathex"></a><a name="compactpathex"></a>CPathT::CompactPathEx

Appelez cette méthode pour tronquer un chemin de fichier pour s’adapter à un nombre donné de caractères en remplaçant les composants du chemin par l’ellipsis.

```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```

### <a name="parameters"></a>Paramètres

*nMaxChars (en)*<br/>
Le nombre maximum de caractères à contenir dans la nouvelle chaîne, y compris le caractère NULL de fin.

*dwFlags*<br/>
Réservé.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).

## <a name="cpathtcpatht"></a><a name="cpatht"></a>CPathT::CPathT

Constructeur.

```
CPathT(PCXSTR pszPath);
CPathT(const CPathT<StringType>& path);
CPathT() throw();
```

### <a name="parameters"></a>Paramètres

*pszPath (pszPath)*<br/>
Le pointeur d’une chaîne de chemin.

*path*<br/>
La corde de chemin.

## <a name="cpathtfileexists"></a><a name="fileexists"></a>CPathT::FileExists

Appelez cette méthode pour vérifier si le fichier à ce nom de chemin existe.

```
BOOL FileExists() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le fichier existe, FALSE autrement.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).

## <a name="cpathtfindextension"></a><a name="findextension"></a>CPathT::FindExtension

Appelez cette méthode pour trouver la position de l’extension du fichier dans le chemin.

```
int FindExtension() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la position du "." précédant l’extension. Si aucune prolongation n’est trouvée, renvoie -1.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).

## <a name="cpathtfindfilename"></a><a name="findfilename"></a>CPathT::FindFileName

Appelez cette méthode pour trouver la position du nom du fichier dans le chemin.

```
int FindFileName() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la position du nom du fichier. Si aucun nom de fichier n’est trouvé, renvoie -1.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).

## <a name="cpathtgetdrivenumber"></a><a name="getdrivenumber"></a>CPathT::GetDriveNumber

Appelez cette méthode pour rechercher le chemin à la recherche d’une lettre d’entraînement dans la plage de 'A' à 'Z' et retourner le numéro d’entraînement correspondant.

```
int GetDriveNumber() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne le numéro d’entraînement en tant qu’integer de 0 à 25 (correspondant à 'A' par 'Z') si le chemin a une lettre d’entraînement, ou -1 autrement.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).

## <a name="cpathtgetextension"></a><a name="getextension"></a>CPathT:GetExtension

Appelez cette méthode pour obtenir l’extension du fichier à partir du chemin.

```
StringType GetExtension() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la prolongation du fichier.

## <a name="cpathtisdirectory"></a><a name="isdirectory"></a>CPathT::IsDirectory

Appelez cette méthode pour vérifier si le chemin est un répertoire valide.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne une valeur non nulle (16) si le chemin est un répertoire, FALSE autrement.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).

## <a name="cpathtisfilespec"></a><a name="isfilespec"></a>CPathT::IsFileSpec

Appelez cette méthode pour rechercher un chemin pour tous les personnages délimiter\\le chemin (par exemple, «:» ou '). S’il n’y a pas de personnages délimiter les chemins présents, le chemin est considéré comme un chemin De file Spec.

```
BOOL IsFileSpec() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI s’il n’y a pas de personnages délimiter le chemin, ou FALSE s’il y a des personnages délimités par le chemin.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).

## <a name="cpathtisprefix"></a><a name="isprefix"></a>CPathT::IsPrefix

Appelez cette méthode pour déterminer si un chemin contient un préfixe valide du type passé par *pszPrefix*.

```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```

### <a name="parameters"></a>Paramètres

*pszPrefix*<br/>
Le préfixe pour lequel rechercher. Un préfixe est l’un\\\\de ces types: "C: ", ".", "..", ".. \\\\".

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le chemin contient le préfixe, ou FALSE autrement.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw).

## <a name="cpathtisrelative"></a><a name="isrelative"></a>CPathT:IsRelative

Appelez cette méthode pour déterminer si le chemin est relatif.

```
BOOL IsRelative() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le chemin est relatif, ou FALSE si elle est absolue.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).

## <a name="cpathtisroot"></a><a name="isroot"></a>CPathT::IsRoot

Appelez cette méthode pour déterminer si le chemin est une racine d’annuaire.

```
BOOL IsRoot() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le chemin est une racine, ou FALSE autrement.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).

## <a name="cpathtissameroot"></a><a name="issameroot"></a>CPathT::IsSameRoot

Appelez cette méthode pour déterminer si un autre chemin a une composante racine commune avec le chemin actuel.

```
BOOL IsSameRoot(PCXSTR pszOther) const;
```

### <a name="parameters"></a>Paramètres

*pszOther*<br/>
L’autre chemin.

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si les deux cordes ont le même composant racine, ou FALSE autrement.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw).

## <a name="cpathtisunc"></a><a name="isunc"></a>CPathT:IsUNC

Appelez cette méthode pour déterminer si le chemin est un chemin valide UNC (convention universelle de nommage) pour un serveur et partager.

```
BOOL IsUNC() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le chemin est un chemin valide UNC, ou FALSE autrement.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).

## <a name="cpathtisuncserver"></a><a name="isuncserver"></a>CPathT:IsUNCServer

Appelez cette méthode pour déterminer si le chemin est un chemin valide UNC (convention universelle de nommage) pour un serveur seulement.

```
BOOL IsUNCServer() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si la chaîne est un chemin UNC valide pour un serveur seulement (pas de nom d’action), ou FALSE autrement.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).

## <a name="cpathtisuncservershare"></a><a name="isuncservershare"></a>CPathT::IsUNCServerShare

Appelez cette méthode pour déterminer si le chemin est un moyen \\ \ valide UNC (convention universelle de nommage) partager chemin,*partage* *de serveur*\ .

```
BOOL IsUNCServerShare() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le chemin \\ \ est dans la*part*du *serveur*\ de forme , ou FALSE autrement.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).

## <a name="cpathtm_strpath"></a><a name="m_strpath"></a>CPathT::m_strPath

Le chemin d'accès.

```
StringType m_strPath;
```

### <a name="remarks"></a>Notes

`StringType`est le paramètre de modèle pour `CPathT`.

## <a name="cpathtmakepretty"></a><a name="makepretty"></a>CPathT::MakePretty

Appelez cette méthode pour convertir un chemin à tous les caractères minuscules pour donner au chemin une apparence cohérente.

```
BOOL MakePretty();
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si le chemin a été converti, ou FALSE autrement.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).

## <a name="cpathtmatchspec"></a><a name="matchspec"></a>CPathT::MatchSpec

Appelez cette méthode pour rechercher le chemin pour une chaîne contenant un type de match wildcard.

```
BOOL MatchSpec(PCXSTR pszSpec) const;
```

### <a name="parameters"></a>Paramètres

*pszSpec*<br/>
Pointeur vers une chaîne non terminée avec le type de fichier pour lequel rechercher. Par exemple, pour vérifier si le fichier sur la trajectoire actuelle est un fichier DOC, *pszSpec* doit être configuré à ".doc".

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si la chaîne correspond, ou FALSE autrement.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).

## <a name="cpathtoperator-"></a><a name="operator_add_eq"></a>CPathT::opérateur

Cet opérateur attache une corde au chemin.

```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```

### <a name="parameters"></a>Paramètres

*pszMore*<br/>
Chaîne à ajouter.

### <a name="return-value"></a>Valeur de retour

Retourne le chemin mis à jour.

## <a name="cpathtoperator-const-stringtype-amp"></a><a name="operator_const_stringtype_amp"></a>CPathT::opérateur const StringType&amp;

Cet opérateur permet de traiter l’objet comme une chaîne.

```
operator const StringType&() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une chaîne représentant le chemin actuel géré par cet objet.

## <a name="cpathtoperator-cpathtpcxstr"></a><a name="operator_cpatht__pcxstr"></a>CPathT::opérateur CPathT::PCXSTR

Cet opérateur permet de traiter l’objet comme une chaîne.

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une chaîne représentant le chemin actuel géré par cet objet.

## <a name="cpathtoperator-stringtype-amp"></a><a name="operator_stringtype_amp"></a>CPathT::opérateur StringType&amp;

Cet opérateur permet de traiter l’objet comme une chaîne.

```
operator StringType&() throw();
```

### <a name="return-value"></a>Valeur de retour

Retourne une chaîne représentant le chemin actuel géré par cet objet.

## <a name="cpathtpcxstr"></a><a name="pcxstr"></a>CPathT::PCXSTR

Un type de chaîne constant.

```
typedef StringType::PCXSTR PCXSTR;
```

### <a name="remarks"></a>Notes

`StringType`est le paramètre de modèle pour `CPathT`.

## <a name="cpathtpxstr"></a><a name="pxstr"></a>CPathT::PXSTR

Type chaîne.

```
typedef StringType::PXSTR PXSTR;
```

### <a name="remarks"></a>Notes

`StringType`est le paramètre de modèle pour `CPathT`.

## <a name="cpathtquotespaces"></a><a name="quotespaces"></a>CPathT::QuoteSpaces

Appelez cette méthode pour enfermer le chemin dans des guillemets s’il contient des espaces.

```cpp
void QuoteSpaces();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).

## <a name="cpathtrelativepathto"></a><a name="relativepathto"></a>CPathT::RelativePathTo

Appelez cette méthode pour créer un chemin relatif d’un fichier ou d’un dossier à un autre.

```
BOOL RelativePathTo(
    PCXSTR pszFrom,
    DWORD dwAttrFrom,
    PCXSTR pszTo,
    DWORD dwAttrTo);
```

### <a name="parameters"></a>Paramètres

*pszDe*<br/>
Le début du chemin relatif.

*dwAttrDe*<br/>
Les attributs du fichier de *pszDe*. Si cette valeur contient FILE_ATTRIBUTE_DIRECTORY, *pszFrom* est supposé être un répertoire; autrement, *pszFrom* est supposé être un fichier.

*pszTo*<br/>
Le point final du chemin relatif.

*dwAttrTo*<br/>
Les attributs du fichier de *pszTo*. Si cette valeur contient FILE_ATTRIBUTE_DIRECTORY, *pszTo* est supposé être un répertoire; autrement, *pszTo* est supposé être un fichier.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).

## <a name="cpathtremoveargs"></a><a name="removeargs"></a>CPathT::SupprimerArgs

Appelez cette méthode pour supprimer tous les arguments de ligne de commande du chemin.

```cpp
void RemoveArgs();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).

## <a name="cpathtremovebackslash"></a><a name="removebackslash"></a>CPathT::RemoveBackslash

Appelez cette méthode pour enlever la barre oblique arrière de fuite du chemin.

```cpp
void RemoveBackslash();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).

## <a name="cpathtremoveblanks"></a><a name="removeblanks"></a>CPathT::RemoveBlanks

Appelez cette méthode pour enlever tous les espaces de tête et de fuite du chemin.

```cpp
void RemoveBlanks();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).

## <a name="cpathtremoveextension"></a><a name="removeextension"></a>CPathT::Supprimerextension

Appelez cette méthode pour supprimer l’extension du fichier du chemin, s’il y en a une.

```cpp
void RemoveExtension();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).

## <a name="cpathtremovefilespec"></a><a name="removefilespec"></a>CPathT::RemoveFileSpec

Appelez cette méthode pour supprimer le nom de fichier de fuite et la barre oblique inverse du chemin, si elle les a.

```
BOOL RemoveFileSpec();
```

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).

## <a name="cpathtrenameextension"></a><a name="renameextension"></a>CPathT::RenameExtension

Appelez cette méthode pour remplacer l’extension du nom de fichier dans le chemin par une nouvelle extension. Si le nom du fichier ne contient pas d’extension, l’extension sera fixée à la fin du chemin.

```
BOOL RenameExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Paramètres

*pszExtension*<br/>
La nouvelle extension du nom de fichier, précédée d’un ". caractère.

### <a name="return-value"></a>Valeur de retour

Retourne TRUE sur le succès, FALSE sur l’échec.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).

## <a name="cpathtskiproot"></a><a name="skiproot"></a>CPathT::SkipRoot

Appelez cette méthode pour analyser un chemin, en ignorant la lettre d’entraînement ou unC (convention universelle de nommage) serveur / partage des parties de chemin.

```
int SkipRoot() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne la position du début du sous-chemin qui suit la racine (lettre d’entraînement ou serveur/partage DE l’UNC).

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).

## <a name="cpathtstrippath"></a><a name="strippath"></a>CPathT::StripPath

Appelez cette méthode pour supprimer la partie de chemin d’un chemin entièrement qualifié et le nom de fichier.

```cpp
void StripPath();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).

## <a name="cpathtstriptoroot"></a><a name="striptoroot"></a>CPathT::StripToRoot

Appelez cette méthode pour supprimer toutes les parties du chemin, sauf pour les informations de racine.

```
BOOL StripToRoot();
```

### <a name="return-value"></a>Valeur de retour

Retourne VRAI si une lettre d’entraînement valide a été trouvée dans le chemin, ou FALSE autrement.

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).

## <a name="cpathtunquotespaces"></a><a name="unquotespaces"></a>CPathT::UnquoteSpaces

Appelez cette méthode pour supprimer les guillemets du début et de la fin d’un chemin.

```cpp
void UnquoteSpaces();
```

### <a name="remarks"></a>Notes

Pour plus d’informations, voir [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).

## <a name="cpathtxchar"></a><a name="xchar"></a>CPathT::XCHAR

Type de caractère.

```
typedef StringType::XCHAR XCHAR;
```

### <a name="remarks"></a>Notes

`StringType`est le paramètre de modèle pour `CPathT`.

## <a name="see-also"></a>Voir aussi

[Classes](../../atl/reference/atl-classes.md)<br/>
[Classe CStringT](../../atl-mfc-shared/reference/cstringt-class.md)
