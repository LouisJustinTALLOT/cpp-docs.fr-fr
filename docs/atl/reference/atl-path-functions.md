---
title: Fonctions ATL Path
ms.date: 11/04/2016
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
ms.openlocfilehash: f3d8fa63e7fd20f8a0d6759fee8417b3fbc29486
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319223"
---
# <a name="atl-path-functions"></a>Fonctions ATL Path

ATL fournit la classe ATLPath pour manipuler les chemins sous la forme de [CPathT](cpatht-class.md). Ce code peut être trouvé dans atlpath.h.

### <a name="related-classes"></a>Classes connexes

|||
|-|-|
|[Classe CPathT](cpatht-class.md)|Cette classe représente un chemin.|

### <a name="related-typedefs"></a>Typedefs connexes

|||
|-|-|
|`CPath`|Une spécialisation de [CPathT](cpatht-class.md) à l’aide `CString`de .|
|`CPathA`|Une spécialisation de [CPathT](cpatht-class.md) à l’aide `CStringA`de .|
|`CPathW`|Une spécialisation de [CPathT](cpatht-class.md) à l’aide `CStringW`de .|

### <a name="functions"></a>Fonctions

|||
|-|-|
|[ATLPath::AddBackslash](#addbackslash)|Cette fonction est un emballage surchargé pour [PathAddBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).|
|[ATLPath::AddExtension](#addextension)|Cette fonction est un emballage surchargé pour [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).|
|[ATLPath::Append](#append)|Cette fonction est un emballage surchargé pour [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).|
|[ATLPath::BuildRoot](#buildroot)|Cette fonction est un emballage surchargé pour [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).|
|[ATLPath::Canonicalize](#canonicalize)|Cette fonction est un emballage surchargé pour [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).|
|[ATLPath::Combine](#combine)|Cette fonction est un emballage surchargé pour [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).|
|[ATLPath::CommonPrefix](#commonprefix)|Cette fonction est un emballage surchargé pour [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).|
|[ATLPath::CompactPath](#compactpath)|Cette fonction est un emballage surchargé pour [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).|
|[ATLPath::CompactPathEx](#compactpathex)|Cette fonction est un emballage surchargé pour [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).|
|[ATLPath::FileExists](#fileexists)|Cette fonction est un emballage surchargé pour [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).|
|[ATLPath::FindExtension](#findextension)|Cette fonction est un emballage surchargé pour [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).|
|[ATLPath::FindFileName](#findfilename)|Cette fonction est un emballage surchargé pour [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).|
|[ATLPath::GetDriveNumber](#getdrivenumber)|Cette fonction est un emballage surchargé pour [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).|
|[ATLPath::IsDirectory](#isdirectory)|Cette fonction est un emballage surchargé pour [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).|
|[ATLPath::IsFileSpec](#isfilespec)|Cette fonction est un emballage surchargé pour [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).|
|[ATLPath::IsPrefix](#isprefix)|Cette fonction est un emballage surchargé pour [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw).|
|[ATLPath::IsRelative](#isrelative)|Cette fonction est un emballage surchargé pour [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).|
|[ATLPath::IsRoot](#isroot)|Cette fonction est un emballage surchargé pour [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).|
|[ATLPath::IsSameRoot](#issameroot)|Cette fonction est un emballage surchargé pour [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw).|
|[ATLPath::IsUNC](#isunc)|Cette fonction est un emballage surchargé pour [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).|
|[ATLPath::IsUNCServer](#isuncserver)|Cette fonction est un emballage surchargé pour [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).|
|[ATLPath::IsUNCServerShare](#isuncservershare)|Cette fonction est un emballage surchargé pour [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).|
|[ATLPath::MakePretty](#makepretty)|Cette fonction est un emballage surchargé pour [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).|
|[ATLPath::MatchSpec](#matchspec)|Cette fonction est un emballage surchargé pour [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).|
|[ATLPath::QuoteSpaces](#quotespaces)|Cette fonction est un emballage surchargé pour [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).|
|[ATLPath::RelativePathTo](#relativepathto)|Cette fonction est un emballage surchargé pour [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).|
|[ATLPath::RemoveArgs](#removeargs)|Cette fonction est un emballage surchargé pour [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).|
|[ATLPath::RemoveBackslash](#removebackslash)|Cette fonction est un emballage surchargé pour [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).|
|[ATLPath::RemoveBlanks](#removeblanks)|Cette fonction est un emballage surchargé pour [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).|
|[ATLPath::RemoveExtension](#removeextension)|Cette fonction est un emballage surchargé pour [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).|
|[ATLPath::RemoveFileSpec](#removefilespec)|Cette fonction est un emballage surchargé pour [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).|
|[ATLPath::RenameExtension](#renameextension)|Cette fonction est un emballage surchargé pour [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).|
|[ATLPath::SkipRoot](#skiproot)|Cette fonction est un emballage surchargé pour [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).|
|[ATLPath::StripPath](#strippath)|Cette fonction est un emballage surchargé pour [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).|
|[ATLPath::StripToRoot](#striptoroot)|Cette fonction est un emballage surchargé pour [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).|
|[ATLPath::UnquoteSpaces](#unquotespaces)|Cette fonction est un emballage surchargé pour [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).|

## <a name="requirements"></a>Spécifications

**En-tête:** atlpath.h

## <a name="atlpathaddbackslash"></a><a name="addbackslash"></a>ATLPath::AddBackSlash

Cette fonction est un emballage surchargé pour [PathAddBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw).

### <a name="syntax"></a>Syntaxe

```
inline char* AddBackslash(char* pszPath);
inline wchar_t* AddBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir [PathAddBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw) pour plus de détails.

## <a name="atlpathaddextension"></a><a name="addextension"></a>ATLPath::AddExtension

Cette fonction est un emballage surchargé pour [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL AddExtension(char* pszPath, const char* pszExtension);
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);
```

### <a name="remarks"></a>Notes

Voir [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw) pour plus de détails.

## <a name="atlpathappend"></a><a name="append"></a>ATLPath::Append

Cette fonction est un emballage surchargé pour [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL Append(char* pszPath, const char* pszMore);
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);
```

### <a name="remarks"></a>Notes

Voir [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw) pour plus de détails.

## <a name="atlpathbuildroot"></a><a name="buildroot"></a>ATLPath::BuildRoot

Cette fonction est un emballage surchargé pour [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw).

### <a name="syntax"></a>Syntaxe

```
inline char* BuildRoot(char* pszPath, int iDrive);
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);
```

### <a name="remarks"></a>Notes

Voir [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw) pour plus de détails.

## <a name="atlpathcanonicalize"></a><a name="canonicalize"></a>ATLPath::Canonicalize

Cette fonction est un emballage surchargé pour [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew).

### <a name="syntax"></a>Syntaxe

```
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);
```

### <a name="remarks"></a>Notes

Voir [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew) pour plus de détails.

## <a name="atlpathcombine"></a><a name="combine"></a>ATLPath::Combinez

Cette fonction est un emballage surchargé pour [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew).

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

Voir PathCombine pour plus de détails.

## <a name="atlpathcommonprefix"></a><a name="commonprefix"></a>ATLPath::CommonPrefix

Cette fonction est un emballage surchargé pour [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw).

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

Voir [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw) pour plus de détails.

## <a name="atlpathcompactpath"></a><a name="compactpath"></a>ATLPath::CompactPath

Cette fonction est un emballage surchargé pour [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw).

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

Voir [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw) pour plus de détails.

## <a name="atlpathcompactpathex"></a><a name="compactpathex"></a>ATLPath::CompactPathEx

Cette fonction est un emballage surchargé pour [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw).

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

Voir [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw) pour plus de détails.

## <a name="atlpathfileexists"></a><a name="fileexists"></a>ATLPath:FileExists

Cette fonction est un emballage surchargé pour [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL FileExists(const char* pszPath);
inline BOOL FileExists(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw) pour plus de détails.

## <a name="atlpathfindextension"></a><a name="findextension"></a>ATLPath::FindExtension

Cette fonction est un emballage surchargé pour [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw).

### <a name="syntax"></a>Syntaxe

```
inline char* FindExtension(const char* pszPath);
inline wchar_t* FindExtension(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw) pour plus de détails.

## <a name="atlpathfindfilename"></a><a name="findfilename"></a>ATLPath::FindFileName

Cette fonction est un emballage surchargé pour [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew).

### <a name="syntax"></a>Syntaxe

```
inline char* FindFileName(const char* pszPath);
inline wchar_t* FindFileName(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) pour plus de détails.

## <a name="atlpathgetdrivenumber"></a><a name="getdrivenumber"></a>ATLPath::GetDriveNumber

Cette fonction est un emballage surchargé pour [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw).

### <a name="syntax"></a>Syntaxe

```
inline int GetDriveNumber(const char* pszPath);
inline int GetDriveNumber(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw) pour plus de détails.

## <a name="atlpathisdirectory"></a><a name="isdirectory"></a>ATLPath:IsDirectory

Cette fonction est un emballage surchargé pour [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw).

```
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir PathIsDirectory pour plus de détails.

## <a name="atlpathisfilespec"></a><a name="isfilespec"></a>ATLPath::IsFileSpec

Cette fonction est un emballage surchargé pour [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsFileSpec(const char* pszPath);
inline BOOL IsFileSpec(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw) pour plus de détails.

## <a name="atlpathisprefix"></a><a name="isprefix"></a>ATLPath::IsPrefix

Cette fonction est un emballage surchargé pour [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw) pour plus de détails.

## <a name="atlpathisrelative"></a><a name="isrelative"></a>ATLPath:IsRelative

Cette fonction est un emballage surchargé pour [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsRelative(const char* pszPath);
inline BOOL IsRelative(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew) pour plus de détails.

## <a name="atlpathisroot"></a><a name="isroot"></a>ATLPath::IsRoot

Cette fonction est un emballage surchargé pour [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsRoot(const char* pszPath);
inline BOOL IsRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw) pour plus de détails.

## <a name="atlpathissameroot"></a><a name="issameroot"></a>ATLPath::IsSameRoot

Cette fonction est un emballage surchargé pour [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);
```

### <a name="remarks"></a>Notes

Voir [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw) pour plus de détails.

## <a name="atlpathisunc"></a><a name="isunc"></a>ATLPath:IsUNC

Cette fonction est un emballage surchargé pour [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsUNC(const char* pszPath);
inline BOOL IsUNC(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw) pour plus de détails.

## <a name="atlpathisuncserver"></a><a name="isuncserver"></a>ATLPath:IsUNCServer

Cette fonction est un emballage surchargé pour [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsUNCServer(const char* pszPath);
inline BOOL IsUNCServer(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw) pour plus de détails.

## <a name="atlpathisuncservershare"></a><a name="isuncservershare"></a>ATLPath::IsUNCServerShare

Cette fonction est un emballage surchargé pour [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).

### <a name="syntax"></a>Syntaxe

```
inline BOOL IsUNCServerShare(const char* pszPath);
inline BOOL IsUNCServerShare(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew) pour plus de détails.

## <a name="atlpathmakepretty"></a><a name="makepretty"></a>ATLPath::MakePretty

Cette fonction est un emballage surchargé pour [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL MakePretty(char* pszPath);
inline BOOL MakePretty(wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw) pour plus de détails.

## <a name="atlpathmatchspec"></a><a name="matchspec"></a>ATLPath::MatchSpec

Cette fonction est un emballage surchargé pour [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);
```

### <a name="remarks"></a>Notes

Voir [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw) pour plus de détails.

## <a name="atlpathquotespaces"></a><a name="quotespaces"></a>ATLPath::QuoteSpaces

Cette fonction est un emballage surchargé pour [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).

### <a name="syntax"></a>Syntaxe

```
inline void QuoteSpaces(char* pszPath);
inline void QuoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw) pour plus de détails.

## <a name="atlpathrelativepathto"></a><a name="relativepathto"></a>ATLPath::RelativePathTo

Cette fonction est un emballage surchargé pour [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).

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

Voir [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow) pour plus de détails.

## <a name="atlpathremoveargs"></a><a name="removeargs"></a>ATLPath::SupprimerArgs

Cette fonction est un emballage surchargé pour [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).

### <a name="syntax"></a>Syntaxe

```
inline void RemoveArgs(char* pszPath);
inline void RemoveArgs(wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw) pour plus de détails.

## <a name="atlpathremovebackslash"></a><a name="removebackslash"></a>ATLPath::RemoveBackslash

Cette fonction est un emballage surchargé pour [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).

### <a name="syntax"></a>Syntaxe

```
inline char* RemoveBackslash(char* pszPath);
inline wchar_t* RemoveBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw) pour plus de détails.

## <a name="atlpathremoveblanks"></a><a name="removeblanks"></a>ATLPath::RemoveBlanks

Cette fonction est un emballage surchargé pour [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).

### <a name="syntax"></a>Syntaxe

```
inline void RemoveBlanks(char* pszPath);
inline void RemoveBlanks(wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw) pour plus de détails.

## <a name="atlpathremoveextension"></a><a name="removeextension"></a>ATLPath::SupprimerExtension

Cette fonction est un emballage surchargé pour [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).

### <a name="syntax"></a>Syntaxe

```
inline void RemoveExtension(char* pszPath);
inline void RemoveExtension(wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw) pour plus de détails.

## <a name="atlpathremovefilespec"></a><a name="removefilespec"></a>ATLPath::RemoveFileSpec

Cette fonction est un emballage surchargé pour [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL RemoveFileSpec(char* pszPath);
inline BOOL RemoveFileSpec(wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw) pour plus de détails.

## <a name="atlpathrenameextension"></a><a name="renameextension"></a>ATLPath:RenameExtension

Cette fonction est un emballage surchargé pour [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL RenameExtension(char* pszPath, const char* pszExt);
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);
```

### <a name="remarks"></a>Notes

Voir [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw) pour plus de détails.

## <a name="atlpathskiproot"></a><a name="skiproot"></a>ATLPath:SkipRoot

Cette fonction est un emballage surchargé pour [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).

### <a name="syntax"></a>Syntaxe

```
inline char* SkipRoot(const char* pszPath);
inline wchar_t* SkipRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw) pour plus de détails.

## <a name="atlpathstrippath"></a><a name="strippath"></a>ATLPath::StripPath

Cette fonction est un emballage surchargé pour [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).

### <a name="syntax"></a>Syntaxe

```
inline void StripPath(char* pszPath);
inline void StripPath(wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw) pour plus de détails.

## <a name="atlpathstriptoroot"></a><a name="striptoroot"></a>ATLPath::StripToRoot

Cette fonction est un emballage surchargé pour [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).

### <a name="syntax"></a>Syntaxe

```
inline BOOL StripToRoot(char* pszPath);
inline BOOL StripToRoot(wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw) pour plus de détails.

## <a name="atlpathunquotespaces"></a><a name="unquotespaces"></a>ATLPath:UnquoteSpaces

Cette fonction est un emballage surchargé pour [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).

### <a name="syntax"></a>Syntaxe

```
inline void UnquoteSpaces(char* pszPath);
inline void UnquoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Notes

Voir [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw) pour plus de détails.
