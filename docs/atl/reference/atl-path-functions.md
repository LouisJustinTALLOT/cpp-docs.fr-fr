---
title: Fonctions de chemin d’accès de l’ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ATL, path
f1_keywords:
- ATLPATH/ATL::ATLPath::AddBackslash
- ATLPATH/ATL::ATLPath::AddExtension
- ATLPATH/ATL::ATLPath::Append
- ATLPATH/ATL::ATLPath::BuildRoot
- ATLPATH/ATL::ATLPath::Canonicalize
- ATLPATH/ATL::ATLPath::Combine
- ATLPATH/ATL::ATLPath::CommonPrefix
- ATLPATH/ATL::ATLPath::CompactPath
- ATLPATH/ATL::ATLPath::CompactPathEx
- ATLPATH/ATL::ATLPath::FileExists
- ATLPATH/ATL::ATLPath::FindExtension
- ATLPATH/ATL::ATLPath::FindFileName
- ATLPATH/ATL::ATLPath::GetDriveNumber
- ATLPATH/ATL::ATLPath::IsDirectory
- ATLPATH/ATL::ATLPath::IsFileSpec
- ATLPATH/ATL::ATLPath::IsPrefix
- ATLPATH/ATL::ATLPath::IsRelative
- ATLPATH/ATL::ATLPath::IsRoot
- ATLPATH/ATL::ATLPath::IsSameRoot
- ATLPATH/ATL::ATLPath::IsUNC
- ATLPATH/ATL::ATLPath::IsUNCServer
- ATLPATH/ATL::ATLPath::IsUNCServerShare
- ATLPATH/ATL::ATLPath::MakePretty
- ATLPATH/ATL::ATLPath::MatchSpec
- ATLPATH/ATL::ATLPath::QuoteSpaces
- ATLPATH/ATL::ATLPath::RelativePathTo
- ATLPATH/ATL::ATLPath::RemoveArgs
- ATLPATH/ATL::ATLPath::RemoveBackslash
- ATLPATH/ATL::ATLPath::RemoveBlanks
- ATLPATH/ATL::ATLPath::RemoveExtension
- ATLPATH/ATL::ATLPath::RemoveFileSpec
- ATLPATH/ATL::ATLPath::RenameExtension
- ATLPATH/ATL::ATLPath::SkipRoot
- ATLPATH/ATL::ATLPath::StripPath
- ATLPATH/ATL::ATLPath::StripToRoot
- ATLPATH/ATL::ATLPath::UnquoteSpaces
ms.assetid: d1ec2b8d-7ec7-43ea-90dd-0a740d2a742b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cdb658b179e3e3488b070203ad7f0909610d4fd8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054642"
---
# <a name="atl-path-functions"></a>Fonctions de chemin d’accès de l’ATL

ATL fournit la classe ATLPath permettant de manipuler des chemins d’accès sous la forme de [CPathT](cpatht-class.md). Vous trouverez ce code dans atlpath.h.

### <a name="related-classes"></a>Classes connexes

|||
|-|-|
|[CPathT, classe](cpatht-class.md)|Cette classe représente un chemin d’accès.|

### <a name="related-typedefs"></a>Typedefs connexes

|||
|-|-|
|`CPath`|Une spécialisation de [CPathT](cpatht-class.md) à l’aide de `CString`.|
|`CPathA`|Une spécialisation de [CPathT](cpatht-class.md) à l’aide de `CStringA`.|
|`CPathW`|Une spécialisation de [CPathT](cpatht-class.md) à l’aide de `CStringW`.|

### <a name="functions"></a>Fonctions

|||
|-|-|
|[ATLPath::AddBackslash](#addbackslash)|Cette fonction est un wrapper surchargé de [PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha).|
|[ATLPath::AddExtension](#addextension)|Cette fonction est un wrapper surchargé de [PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona).|
|[ATLPath::Append](#append)|Cette fonction est un wrapper surchargé de [PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda).|
|[ATLPath::BuildRoot](#buildroot)|Cette fonction est un wrapper surchargé de [PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota).|
|[ATLPath::Canonicalize](#canonicalize)|Cette fonction est un wrapper surchargé de [PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea).|
|[ATLPath::Combine](#combine)|Cette fonction est un wrapper surchargé de [PathCombine](/windows/desktop/api/shlwapi/nf-shlwapi-pathcombinea).|
|[ATLPath::CommonPrefix](#commonprefix)|Cette fonction est un wrapper surchargé de [PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa).|
|[ATLPath::CompactPath](#compactpath)|Cette fonction est un wrapper surchargé de [PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha).|
|[ATLPath::CompactPathEx](#compactpathex)|Cette fonction est un wrapper surchargé de [PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa).|
|[ATLPath::FileExists](#fileexists)|Cette fonction est un wrapper surchargé de [PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa).|
|[ATLPath::FindExtension](#findextension)|Cette fonction est un wrapper surchargé de [PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona).|
|[ATLPath::FindFileName](#findfilename)|Cette fonction est un wrapper surchargé de [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea).|
|[ATLPath::GetDriveNumber](#getdrivenumber)|Cette fonction est un wrapper surchargé de [PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera).|
|[ATLPath::IsDirectory](#isdirectory)|Cette fonction est un wrapper surchargé de [PathIsDirectory](/windows/desktop/api/shlwapi/nf-shlwapi-pathisdirectorya).|
|[ATLPath::IsFileSpec](#isfilespec)|Cette fonction est un wrapper surchargé de [PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca).|
|[ATLPath::IsPrefix](#isprefix)|Cette fonction est un wrapper surchargé de [PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa).|
|[ATLPath::IsRelative](#isrelative)|Cette fonction est un wrapper surchargé de [PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea).|
|[ATLPath::IsRoot](#isroot)|Cette fonction est un wrapper surchargé de [PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota).|
|[ATLPath::IsSameRoot](#issameroot)|Cette fonction est un wrapper surchargé de [PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota).|
|[ATLPath::IsUNC](#isunc)|Cette fonction est un wrapper surchargé de [PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca).|
|[ATLPath::IsUNCServer](#isuncserver)|Cette fonction est un wrapper surchargé de [PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera).|
|[ATLPath::IsUNCServerShare](#isuncservershare)|Cette fonction est un wrapper surchargé de [PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea).|
|[ATLPath::MakePretty](#makepretty)|Cette fonction est un wrapper surchargé de [PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya).|
|[ATLPath::MatchSpec](#matchspec)|Cette fonction est un wrapper surchargé de [PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca).|
|[ATLPath::QuoteSpaces](#quotespaces)|Cette fonction est un wrapper surchargé de [PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa).|
|[ATLPath::RelativePathTo](#relativepathto)|Cette fonction est un wrapper surchargé de [PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa).|
|[ATLPath::RemoveArgs](#removeargs)|Cette fonction est un wrapper surchargé de [PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa).|
|[ATLPath::RemoveBackslash](#removebackslash)|Cette fonction est un wrapper surchargé de [PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha).|
|[ATLPath::RemoveBlanks](#removeblanks)|Cette fonction est un wrapper surchargé de [PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa).|
|[ATLPath::RemoveExtension](#removeextension)|Cette fonction est un wrapper surchargé de [PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona).|
|[ATLPath::RemoveFileSpec](#removefilespec)|Cette fonction est un wrapper surchargé de [PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca).|
|[ATLPath::RenameExtension](#renameextension)|Cette fonction est un wrapper surchargé de [PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona).|
|[ATLPath::SkipRoot](#skiproot)|Cette fonction est un wrapper surchargé de [PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota).|
|[ATLPath::StripPath](#strippath)|Cette fonction est un wrapper surchargé de [PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha).|
|[ATLPath::StripToRoot](#striptoroot)|Cette fonction est un wrapper surchargé de [PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota).|
|[ATLPath::UnquoteSpaces](#unquotespaces)|Cette fonction est un wrapper surchargé de [PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa).|

## <a name="requirements"></a>Configuration requise

**En-tête :** atlpath.h

## <a name="addbackslash"></a> ATLPath::AddBackSlash

Cette fonction est un wrapper surchargé de [PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha).

### <a name="syntax"></a>Syntaxe

```
inline char* AddBackslash(char* pszPath);
inline wchar_t* AddBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Consultez [PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha) pour plus d’informations.

## <a name="addextension"></a> ATLPath::AddExtension

Cette fonction est un wrapper surchargé de [PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona).

### <a name="syntax"></a>Syntaxe

```
inline BOOL AddExtension(char* pszPath, const char* pszExtension);
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);
```

### <a name="remarks"></a>Notes

Consultez [PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona) pour plus d’informations.

## <a name="append"></a> ATLPath::Append

Cette fonction est un wrapper surchargé de [PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda).

### <a name="syntax"></a>Syntaxe

```
inline BOOL Append(char* pszPath, const char* pszMore);
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);
```

### <a name="remarks"></a>Notes

Consultez [PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda) pour plus d’informations.

## <a name="buildroot"></a> ATLPath::BuildRoot

Cette fonction est un wrapper surchargé de [PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota).

### <a name="syntax"></a>Syntaxe

```
inline char* BuildRoot(char* pszPath, int iDrive);
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);
```

### <a name="remarks"></a>Notes

Consultez [PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota) pour plus d’informations.

## <a name="canonicalize"></a> ATLPath::Canonicalize

Cette fonction est un wrapper surchargé de [PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea).

### <a name="syntax"></a>Syntaxe

```
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);
```

### <a name="remarks"></a>Notes

Consultez [PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea) pour plus d’informations.

## <a name="combine"></a> ATLPath::Combine

Cette fonction est un wrapper surchargé de [PathCombine](/windows/desktop/api/shlwapi/nf-shlwapi-pathcombinea).

### <a name="syntax"></a>Syntaxe

```
inline char* Combine(
   char* pszDest,
   const char* pszDir,
   const char* pszFile
);

inline wchar_t* Combine(
   wchar_t* pszDest,
   const wchar_t* pszDir,
   const wchar_t* pszFile);
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez PathCombine.

## <a name="commonprefix"></a> ATLPath::CommonPrefix

Cette fonction est un wrapper surchargé de [PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa).

### <a name="syntax"></a>Syntaxe

```
inline int CommonPrefix(
   const char* pszFile1,
   const char* pszFile2,
   char* pszDest);

inline int CommonPrefix(
   const wchar_t* pszFile1,
   const wchar_t* pszFile2,
   wchar_t* pszDest);
```

### <a name="remarks"></a>Notes

Consultez [PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa) pour plus d’informations.

## <a name="compactpath"></a> ATLPath::CompactPath

Cette fonction est un wrapper surchargé de [PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha).

### <a name="syntax"></a>Syntaxe

```
inline BOOL CompactPath(
   HDC hDC,
   char* pszPath,
   UINT dx);

inline BOOL CompactPath(
   HDC hDC,
   wchar_t* pszPath,
   UINT dx);
```

### <a name="remarks"></a>Notes

Consultez [PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha) pour plus d’informations.

## <a name="compactpathex"></a> ATLPath::CompactPathEx

Cette fonction est un wrapper surchargé de [PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa).

### <a name="syntax"></a>Syntaxe

```
inline BOOL CompactPathEx(
   char* pszDest,
   const char* pszSrc,
   UINT nMaxChars,
   DWORD dwFlags);

inline BOOL CompactPathEx(
   wchar_t* pszDest,
   const wchar_t* pszSrc,
   UINT nMaxChars,
   DWORD dwFlags);
```

### <a name="remarks"></a>Notes

Consultez [PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa) pour plus d’informations.

## <a name="fileexists"></a> ATLPath::FileExists

Cette fonction est un wrapper surchargé de [PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa).

### <a name="syntax"></a>Syntaxe

```
inline BOOL FileExists(const char* pszPath);
inline BOOL FileExists(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Consultez [PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa) pour plus d’informations.

## <a name="findextension"></a> ATLPath::FindExtension

Cette fonction est un wrapper surchargé de [PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona).

### <a name="syntax"></a>Syntaxe

```
inline char* FindExtension(const char* pszPath);
inline wchar_t* FindExtension(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Consultez [PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona) pour plus d’informations.

## <a name="findfilename"></a> ATLPath::FindFileName

Cette fonction est un wrapper surchargé de [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea).

### <a name="syntax"></a>Syntaxe

```
inline char* FindFileName(const char* pszPath);
inline wchar_t* FindFileName(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Consultez [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea) pour plus d’informations.

## <a name="getdrivenumber"></a> ATLPath::GetDriveNumber

Cette fonction est un wrapper surchargé de [PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera).

### <a name="syntax"></a>Syntaxe

```
inline int GetDriveNumber(const char* pszPath);
inline int GetDriveNumber(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Consultez [PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera) pour plus d’informations.

## <a name="isdirectory"></a>  ATLPath::IsDirectory

Cette fonction est un wrapper surchargé de [PathIsDirectory](/windows/desktop/api/shlwapi/nf-shlwapi-pathisdirectorya).

```
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Pour plus d’informations, consultez PathIsDirectory.

## <a name="isfilespec"></a> ATLPath::IsFileSpec

Cette fonction est un wrapper surchargé de [PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsFileSpec(const char* pszPath);
inline BOOL IsFileSpec(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Consultez [PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca) pour plus d’informations.

## <a name="isprefix"></a> ATLPath::IsPrefix

Cette fonction est un wrapper surchargé de [PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Consultez [PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa) pour plus d’informations.

## <a name="isrelative"></a> ATLPath::IsRelative

Cette fonction est un wrapper surchargé de [PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsRelative(const char* pszPath);
inline BOOL IsRelative(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Consultez [PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea) pour plus d’informations.

## <a name="isroot"></a> ATLPath::IsRoot

Cette fonction est un wrapper surchargé de [PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsRoot(const char* pszPath);
inline BOOL IsRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Consultez [PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota) pour plus d’informations.

## <a name="issameroot"></a> ATLPath::IsSameRoot

Cette fonction est un wrapper surchargé de [PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);
```

### <a name="remarks"></a>Notes

Consultez [PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota) pour plus d’informations.

## <a name="isunc"></a> ATLPath::IsUNC

Cette fonction est un wrapper surchargé de [PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsUNC(const char* pszPath);
inline BOOL IsUNC(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Consultez [PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca) pour plus d’informations.

## <a name="isuncserver"></a> ATLPath::IsUNCServer

Cette fonction est un wrapper surchargé de [PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsUNCServer(const char* pszPath);
inline BOOL IsUNCServer(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Consultez [PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera) pour plus d’informations.

## <a name="isuncservershare"></a> ATLPath::IsUNCServerShare

Cette fonction est un wrapper surchargé de [PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsUNCServerShare(const char* pszPath);
inline BOOL IsUNCServerShare(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Consultez [PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea) pour plus d’informations.

## <a name="makepretty"></a> ATLPath::MakePretty

Cette fonction est un wrapper surchargé de [PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya).

### <a name="syntax"></a>Syntaxe

```
inline BOOL MakePretty(char* pszPath);
inline BOOL MakePretty(wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Consultez [PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya) pour plus d’informations.

## <a name="matchspec"></a> ATLPath::MatchSpec

Cette fonction est un wrapper surchargé de [PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca).

### <a name="syntax"></a>Syntaxe

```
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);
```

### <a name="remarks"></a>Notes

Consultez [PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca) pour plus d’informations.

## <a name="quotespaces"></a> ATLPath::QuoteSpaces

Cette fonction est un wrapper surchargé de [PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa).

### <a name="syntax"></a>Syntaxe

```
inline void QuoteSpaces(char* pszPath);
inline void QuoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Consultez [PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa) pour plus d’informations.

## <a name="relativepathto"></a> ATLPath::RelativePathTo

Cette fonction est un wrapper surchargé de [PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa).

### <a name="syntax"></a>Syntaxe

```
inline BOOL RelativePathTo(
   char* pszPath,
   const char* pszFrom,
   DWORD dwAttrFrom,
   const char* pszTo,
   DWORD dwAttrTo);

inline BOOL RelativePathTo(
   wchar_t* pszPath,
   const wchar_t* pszFrom,
   DWORD dwAttrFrom,
   const wchar_t* pszTo,
   DWORD dwAttrTo);
```

### <a name="remarks"></a>Notes

Consultez [PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa) pour plus d’informations.

## <a name="removeargs"></a> ATLPath::RemoveArgs

Cette fonction est un wrapper surchargé de [PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa).

### <a name="syntax"></a>Syntaxe

```
inline void RemoveArgs(char* pszPath);
inline void RemoveArgs(wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Consultez [PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa) pour plus d’informations.

## <a name="removebackslash"></a> ATLPath::RemoveBackslash

Cette fonction est un wrapper surchargé de [PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha).

### <a name="syntax"></a>Syntaxe

```
inline char* RemoveBackslash(char* pszPath);
inline wchar_t* RemoveBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Consultez [PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha) pour plus d’informations.

## <a name="removeblanks"></a> ATLPath::RemoveBlanks

Cette fonction est un wrapper surchargé de [PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa).

### <a name="syntax"></a>Syntaxe

```
inline void RemoveBlanks(char* pszPath);
inline void RemoveBlanks(wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Consultez [PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa) pour plus d’informations.

## <a name="removeextension"></a> ATLPath::RemoveExtension

Cette fonction est un wrapper surchargé de [PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona).

### <a name="syntax"></a>Syntaxe

```
inline void RemoveExtension(char* pszPath);
inline void RemoveExtension(wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Consultez [PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona) pour plus d’informations.

## <a name="removefilespec"></a> ATLPath::RemoveFileSpec

Cette fonction est un wrapper surchargé de [PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca).

### <a name="syntax"></a>Syntaxe

```
inline BOOL RemoveFileSpec(char* pszPath);
inline BOOL RemoveFileSpec(wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Consultez [PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca) pour plus d’informations.

## <a name="renameextension"></a> ATLPath::RenameExtension

Cette fonction est un wrapper surchargé de [PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona).

### <a name="syntax"></a>Syntaxe

```
inline BOOL RenameExtension(char* pszPath, const char* pszExt);
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);
```

### <a name="remarks"></a>Notes

Consultez [PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona) pour plus d’informations.

## <a name="skiproot"></a> ATLPath::SkipRoot

Cette fonction est un wrapper surchargé de [PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota).

### <a name="syntax"></a>Syntaxe

```
inline char* SkipRoot(const char* pszPath);
inline wchar_t* SkipRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Consultez [PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota) pour plus d’informations.

## <a name="strippath"></a> ATLPath::StripPath

Cette fonction est un wrapper surchargé de [PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha).

### <a name="syntax"></a>Syntaxe

```
inline void StripPath(char* pszPath);
inline void StripPath(wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Consultez [PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha) pour plus d’informations.

## <a name="striptoroot"></a> ATLPath::StripToRoot

Cette fonction est un wrapper surchargé de [PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota).

### <a name="syntax"></a>Syntaxe

```
inline BOOL StripToRoot(char* pszPath);
inline BOOL StripToRoot(wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Consultez [PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota) pour plus d’informations.

## <a name="unquotespaces"></a> ATLPath::UnquoteSpaces

Cette fonction est un wrapper surchargé de [PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa).

### <a name="syntax"></a>Syntaxe

```
inline void UnquoteSpaces(char* pszPath);
inline void UnquoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Consultez [PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa) pour plus d’informations.

