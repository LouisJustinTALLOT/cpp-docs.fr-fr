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
ms.openlocfilehash: ad0db4641731f4c92550fad075b759957383c52a
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2018
ms.locfileid: "39027574"
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
|[ATLPath::AddBackslash](#addbackslash)|Cette fonction est un wrapper surchargé de [PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561).|  
|[ATLPath::AddExtension](#addextension)|Cette fonction est un wrapper surchargé de [PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563).|  
|[ATLPath::Append](#append)|Cette fonction est un wrapper surchargé de [PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565).|  
|[ATLPath::BuildRoot](#buildroot)|Cette fonction est un wrapper surchargé de [PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567).|  
|[ATLPath::Canonicalize](#canonicalize)|Cette fonction est un wrapper surchargé de [PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569).|  
|[ATLPath::Combine](#combine)|Cette fonction est un wrapper surchargé de [PathCombine](http://msdn.microsoft.com/library/windows/desktop/bb773571).|  
|[ATLPath::CommonPrefix](#commonprefix)|Cette fonction est un wrapper surchargé de [PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574).|  
|[ATLPath::CompactPath](#compactpath)|Cette fonction est un wrapper surchargé de [PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575).|  
|[ATLPath::CompactPathEx](#compactpathex)|Cette fonction est un wrapper surchargé de [PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578).|  
|[ATLPath::FileExists](#fileexists)|Cette fonction est un wrapper surchargé de [PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584).|  
|[ATLPath::FindExtension](#findextension)|Cette fonction est un wrapper surchargé de [PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587).|  
|[ATLPath::FindFileName](#findfilename)|Cette fonction est un wrapper surchargé de [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589).|  
|[ATLPath::GetDriveNumber](#getdrivenumber)|Cette fonction est un wrapper surchargé de [PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612).|  
|[ATLPath::IsDirectory](#isdirectory)|Cette fonction est un wrapper surchargé de [PathIsDirectory](http://msdn.microsoft.com/library/windows/desktop/bb773621).|  
|[ATLPath::IsFileSpec](#isfilespec)|Cette fonction est un wrapper surchargé de [PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627).|  
|[ATLPath::IsPrefix](#isprefix)|Cette fonction est un wrapper surchargé de [PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650).|  
|[ATLPath::IsRelative](#isrelative)|Cette fonction est un wrapper surchargé de [PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660).|  
|[ATLPath::IsRoot](#isroot)|Cette fonction est un wrapper surchargé de [PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674).|  
|[ATLPath::IsSameRoot](#issameroot)|Cette fonction est un wrapper surchargé de [PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687).|  
|[ATLPath::IsUNC](#isunc)|Cette fonction est un wrapper surchargé de [PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712).|  
|[ATLPath::IsUNCServer](#isuncserver)|Cette fonction est un wrapper surchargé de [PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722).|  
|[ATLPath::IsUNCServerShare](#isuncservershare)|Cette fonction est un wrapper surchargé de [PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723).|  
|[ATLPath::MakePretty](#makepretty)|Cette fonction est un wrapper surchargé de [PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725).|  
|[ATLPath::MatchSpec](#matchspec)|Cette fonction est un wrapper surchargé de [PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727).|  
|[ATLPath::QuoteSpaces](#quotespaces)|Cette fonction est un wrapper surchargé de [PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739).|  
|[ATLPath::RelativePathTo](#relativepathto)|Cette fonction est un wrapper surchargé de [PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740).|  
|[ATLPath::RemoveArgs](#removeargs)|Cette fonction est un wrapper surchargé de [PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742).|  
|[ATLPath::RemoveBackslash](#removebackslash)|Cette fonction est un wrapper surchargé de [PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743).|  
|[ATLPath::RemoveBlanks](#removeblanks)|Cette fonction est un wrapper surchargé de [PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745).|  
|[ATLPath::RemoveExtension](#removeextension)|Cette fonction est un wrapper surchargé de [PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746).|  
|[ATLPath::RemoveFileSpec](#removefilespec)|Cette fonction est un wrapper surchargé de [PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748).|  
|[ATLPath::RenameExtension](#renameextension)|Cette fonction est un wrapper surchargé de [PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749).|  
|[ATLPath::SkipRoot](#skiproot)|Cette fonction est un wrapper surchargé de [PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754).|  
|[ATLPath::StripPath](#strippath)|Cette fonction est un wrapper surchargé de [PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756).|  
|[ATLPath::StripToRoot](#striptoroot)|Cette fonction est un wrapper surchargé de [PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757).|  
|[ATLPath::UnquoteSpaces](#unquotespaces)|Cette fonction est un wrapper surchargé de [PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763).|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** atlpath.h  

## <a name="addbackslash"></a> ATLPath::AddBackSlash

Cette fonction est un wrapper surchargé de [PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline char* AddBackslash(char* pszPath);  
inline wchar_t* AddBackslash(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561) pour plus d’informations.  
  
 
  

## <a name="addextension"></a> ATLPath::AddExtension
 Cette fonction est un wrapper surchargé de [PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL AddExtension(char* pszPath, const char* pszExtension);  
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563) pour plus d’informations. 
  
## <a name="append"></a> ATLPath::Append
 Cette fonction est un wrapper surchargé de [PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL Append(char* pszPath, const char* pszMore);  
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565) pour plus d’informations.  
  
 
  

## <a name="buildroot"></a> ATLPath::BuildRoot
 Cette fonction est un wrapper surchargé de [PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline char* BuildRoot(char* pszPath, int iDrive);  
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567) pour plus d’informations.  
  
 
  

## <a name="canonicalize"></a> ATLPath::Canonicalize
 Cette fonction est un wrapper surchargé de [PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);  
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569) pour plus d’informations.  
  
 
  

## <a name="combine"></a> ATLPath::Combine 
Cette fonction est un wrapper surchargé de [PathCombine](https://msdn.microsoft.com/library/windows/desktop/bb773571).  

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
 Cette fonction est un wrapper surchargé de [PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574).  
  
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
 Consultez [PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574) pour plus d’informations.  
  
 
  

## <a name="compactpath"></a> ATLPath::CompactPath
 Cette fonction est un wrapper surchargé de [PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575).  
  
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
 Consultez [PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575) pour plus d’informations.  
  
 
  

## <a name="compactpathex"></a> ATLPath::CompactPathEx
 Cette fonction est un wrapper surchargé de [PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578).  
  
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
 Consultez [PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578) pour plus d’informations.  
  
 
  

## <a name="fileexists"></a> ATLPath::FileExists
 Cette fonction est un wrapper surchargé de [PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL FileExists(const char* pszPath);  
inline BOOL FileExists(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584) pour plus d’informations.  
  
 
  

## <a name="findextension"></a> ATLPath::FindExtension
 Cette fonction est un wrapper surchargé de [PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline char* FindExtension(const char* pszPath);  
inline wchar_t* FindExtension(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587) pour plus d’informations.  
  
 
  

## <a name="findfilename"></a> ATLPath::FindFileName
 Cette fonction est un wrapper surchargé de [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline char* FindFileName(const char* pszPath);  
inline wchar_t* FindFileName(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589) pour plus d’informations.  
  
 
  

## <a name="getdrivenumber"></a> ATLPath::GetDriveNumber  
 Cette fonction est un wrapper surchargé de [PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline int GetDriveNumber(const char* pszPath);  
inline int GetDriveNumber(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612) pour plus d’informations.  
  
 


## <a name="isdirectory"></a>  ATLPath::IsDirectory 
Cette fonction est un wrapper surchargé de [PathIsDirectory](https://msdn.microsoft.com/library/windows/desktop/bb773621).

```  
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```  
### <a name="remarks"></a>Notes
Pour plus d’informations, consultez PathIsDirectory.  

## <a name="isfilespec"></a> ATLPath::IsFileSpec
 Cette fonction est un wrapper surchargé de [PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL IsFileSpec(const char* pszPath);  
inline BOOL IsFileSpec(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627) pour plus d’informations.  
  
 
  

## <a name="isprefix"></a> ATLPath::IsPrefix
 Cette fonction est un wrapper surchargé de [PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);  
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650) pour plus d’informations.  
  
 
  

## <a name="isrelative"></a> ATLPath::IsRelative
 Cette fonction est un wrapper surchargé de [PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL IsRelative(const char* pszPath);  
inline BOOL IsRelative(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660) pour plus d’informations.  
  
 
  

## <a name="isroot"></a> ATLPath::IsRoot
 Cette fonction est un wrapper surchargé de [PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL IsRoot(const char* pszPath);  
inline BOOL IsRoot(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674) pour plus d’informations.  
  
 
  

## <a name="issameroot"></a> ATLPath::IsSameRoot
 Cette fonction est un wrapper surchargé de [PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);  
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687) pour plus d’informations.  
  
 
  

## <a name="isunc"></a> ATLPath::IsUNC
 Cette fonction est un wrapper surchargé de [PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL IsUNC(const char* pszPath);  
inline BOOL IsUNC(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712) pour plus d’informations.  
  
 
  

## <a name="isuncserver"></a> ATLPath::IsUNCServer
 Cette fonction est un wrapper surchargé de [PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL IsUNCServer(const char* pszPath);  
inline BOOL IsUNCServer(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722) pour plus d’informations.  
  
 
  

## <a name="isuncservershare"></a> ATLPath::IsUNCServerShare
 Cette fonction est un wrapper surchargé de [PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL IsUNCServerShare(const char* pszPath);  
inline BOOL IsUNCServerShare(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723) pour plus d’informations.  
  
 
  

## <a name="makepretty"></a> ATLPath::MakePretty
 Cette fonction est un wrapper surchargé de [PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL MakePretty(char* pszPath);  
inline BOOL MakePretty(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725) pour plus d’informations.  
  
 
  

## <a name="matchspec"></a> ATLPath::MatchSpec  
 Cette fonction est un wrapper surchargé de [PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);  
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727) pour plus d’informations.  
  
 
  

## <a name="quotespaces"></a> ATLPath::QuoteSpaces  
 Cette fonction est un wrapper surchargé de [PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline void QuoteSpaces(char* pszPath);  
inline void QuoteSpaces(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739) pour plus d’informations.  
  
 
  

## <a name="relativepathto"></a> ATLPath::RelativePathTo
 Cette fonction est un wrapper surchargé de [PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740).  
  
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
 Consultez [PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740) pour plus d’informations.  
  
 
  

## <a name="removeargs"></a> ATLPath::RemoveArgs  
 Cette fonction est un wrapper surchargé de [PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline void RemoveArgs(char* pszPath);  
inline void RemoveArgs(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742) pour plus d’informations.  
  
 
  

## <a name="removebackslash"></a> ATLPath::RemoveBackslash
 Cette fonction est un wrapper surchargé de [PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline char* RemoveBackslash(char* pszPath);  
inline wchar_t* RemoveBackslash(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743) pour plus d’informations.  
  
 
  

## <a name="removeblanks"></a> ATLPath::RemoveBlanks
 Cette fonction est un wrapper surchargé de [PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline void RemoveBlanks(char* pszPath);  
inline void RemoveBlanks(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745) pour plus d’informations.  
  
 
  

## <a name="removeextension"></a> ATLPath::RemoveExtension
 Cette fonction est un wrapper surchargé de [PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline void RemoveExtension(char* pszPath);  
inline void RemoveExtension(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746) pour plus d’informations.  
  
 
  

## <a name="removefilespec"></a> ATLPath::RemoveFileSpec
 Cette fonction est un wrapper surchargé de [PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL RemoveFileSpec(char* pszPath);  
inline BOOL RemoveFileSpec(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748) pour plus d’informations.  
  
 
  

## <a name="renameextension"></a> ATLPath::RenameExtension
 Cette fonction est un wrapper surchargé de [PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL RenameExtension(char* pszPath, const char* pszExt);  
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749) pour plus d’informations.  
  
 
  

## <a name="skiproot"></a> ATLPath::SkipRoot
 Cette fonction est un wrapper surchargé de [PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline char* SkipRoot(const char* pszPath);  
inline wchar_t* SkipRoot(const wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754) pour plus d’informations.  
  
 
  

## <a name="strippath"></a> ATLPath::StripPath
 Cette fonction est un wrapper surchargé de [PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline void StripPath(char* pszPath);  
inline void StripPath(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756) pour plus d’informations.  
  
 
  


## <a name="striptoroot"></a> ATLPath::StripToRoot
 Cette fonction est un wrapper surchargé de [PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline BOOL StripToRoot(char* pszPath);  
inline BOOL StripToRoot(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757) pour plus d’informations.  
  
 
  

## <a name="unquotespaces"></a> ATLPath::UnquoteSpaces
 Cette fonction est un wrapper surchargé de [PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
inline void UnquoteSpaces(char* pszPath);  
inline void UnquoteSpaces(wchar_t* pszPath);  
```  
  
### <a name="remarks"></a>Notes  
 Consultez [PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763) pour plus d’informations.  
  
 
  
 
