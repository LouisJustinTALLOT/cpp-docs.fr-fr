---
title: Classe de CPathT | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CPathT class
ms.assetid: eba4137d-1fd2-4b44-a2e1-0944db64df3c
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 8cbd91ae1c4318788b38b2daaa7721d1a29fca98
ms.lasthandoff: 02/24/2017

---
# <a name="cpatht-class"></a>CPathT (classe)
Cette classe représente un chemin d’accès.  
  
> [!IMPORTANT]
>  Cette classe et ses membres ne peut pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename StringType>
class CPathT
```  
  
#### <a name="parameters"></a>Paramètres  
 `StringType`  
 La classe de chaînes ATL et MFC à utiliser pour le chemin d’accès (voir [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)).  
  
## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CPathT::PCXSTR](#pcxstr)|Un type de chaîne constante.|  
|[CPathT::PXSTR](#pxstr)|Un type string.|  
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
|[CPathT::Canonicalize](#canonicalize)|Appelez cette méthode pour convertir le chemin d’accès au format canonique.|  
|[CPathT::Combine](#combine)|Appelez cette méthode pour concaténer une chaîne représentant un nom de répertoire et une chaîne représentant un nom de chemin d’accès du fichier dans un chemin d’accès.|  
|[CPathT::CommonPrefix](#commonprefix)|Appelez cette méthode pour déterminer si le chemin d’accès spécifié partage un préfixe commun avec le chemin d’accès actuel.|  
|[CPathT::CompactPath](#compactpath)|Appelez cette méthode pour tronquer un chemin d’accès d’ajuster au sein d’une largeur en pixels donné en remplacement des composants de chemin d’accès avec les points de suspension.|  
|[CPathT::CompactPathEx](#compactpathex)|Appelez cette méthode pour tronquer un chemin d’accès à un nombre donné de caractères en remplacement des composants de chemin d’accès avec les points de suspension.|  
|[CPathT::FileExists](#fileexists)|Appelez cette méthode pour vérifier si le fichier à ce nom de chemin d’accès existe.|  
|[CPathT::FindExtension](#findextension)|Appelez cette méthode pour rechercher la position de l’extension de fichier dans le chemin d’accès.|  
|[CPathT::FindFileName](#findfilename)|Appelez cette méthode pour trouver la position du nom de fichier dans le chemin d’accès.|  
|[CPathT::GetDriveNumber](#getdrivenumber)|Appelez cette méthode pour rechercher le chemin d’accès pour une lettre de lecteur dans la plage de 'A' à 'Z' et retourner le nombre de lecteur correspondant.|  
|[CPathT::GetExtension](#getextension)|Appelez cette méthode pour obtenir l’extension de fichier dans le chemin d’accès.|  
|[CPathT::IsDirectory](#isdirectory)|Appelez cette méthode pour vérifier si le chemin d’accès est un répertoire valide.|  
|[CPathT::IsFileSpec](#isfilespec)|Appelez cette méthode pour rechercher un chemin d’accès pour tous les caractères de délimitation de chemin d’accès (par exemple, ' :' ou '\\'). S’il n’y a aucun caractère délimiteur de chemin d’accès existe, le chemin d’accès est considéré comme un chemin d’accès de la spécification de fichier.|  
|[CPathT::IsPrefix](#isprefix)|Appelez cette méthode pour déterminer si un chemin d’accès contient un préfixe valide du type passé `pszPrefix`.|  
|[CPathT::IsRelative](#isrelative)|Appelez cette méthode pour déterminer si le chemin d’accès est relatif.|  
|[CPathT::IsRoot](#isroot)|Appelez cette méthode pour déterminer si le chemin d’accès est un répertoire racine.|  
|[CPathT::IsSameRoot](#issameroot)|Appelez cette méthode pour déterminer si un autre chemin d’accès est un composant racine commun avec le chemin d’accès actuel.|  
|[CPathT::IsUNC](#isunc)|Appelez cette méthode pour déterminer si le chemin d’accès est un chemin d’accès UNC (convention de dénomination universelle) valide pour un serveur et partager.|  
|[CPathT::IsUNCServer](#isuncserver)|Appelez cette méthode pour déterminer si le chemin d’accès est un chemin d’accès UNC (convention de dénomination universelle) valide pour un seul serveur.|  
|[CPathT::IsUNCServerShare](#isuncservershare)|Appelez cette méthode pour déterminer si le chemin d’accès est un chemin de partage UNC (convention de dénomination universelle) valid, \\ \  *server*\ *partager*.|  
|[CPathT::MakePretty](#makepretty)|Appelez cette méthode pour convertir un chemin d’accès à tous les caractères en minuscules pour donner le chemin d’accès une apparence cohérente.|  
|[CPathT::MatchSpec](#matchspec)|Appelez cette méthode pour rechercher le chemin d’accès d’une chaîne contenant un type de correspondance de caractère générique.|  
|[CPathT::QuoteSpaces](#quotespaces)|Appelez cette méthode pour délimiter le chemin d’accès entre guillemets si elle contient des espaces.|  
|[CPathT::RelativePathTo](#relativepathto)|Appelez cette méthode pour créer un chemin d’accès relatif à partir d’un fichier ou dossier à un autre.|  
|[CPathT::RemoveArgs](#removeargs)|Appelez cette méthode pour supprimer tous les arguments de ligne de commande du chemin d’accès.|  
|[CPathT::RemoveBackslash](#removebackslash)|Appelez cette méthode pour supprimer de la barre oblique de fin du chemin d’accès.|  
|[CPathT::RemoveBlanks](#removeblanks)|Appelez cette méthode pour supprimer tous les espaces de début et de fin du chemin d’accès.|  
|[CPathT::RemoveExtension](#removeextension)|Appelez cette méthode pour supprimer l’extension de fichier du chemin d’accès, le cas échéant.|  
|[CPathT::RemoveFileSpec](#removefilespec)|Appelez cette méthode pour supprimer le chemin d’accès, le nom du fichier à droite et la barre oblique inverse si elle possède les.|  
|[CPathT::RenameExtension](#renameextension)|Appelez cette méthode pour remplacer l’extension de nom de fichier dans le chemin d’accès avec une nouvelle extension. Si le nom de fichier ne contient pas une extension, l’extension est jointes à la fin de la chaîne.|  
|[CPathT::SkipRoot](#skiproot)|Appelez cette méthode pour analyser un chemin d’accès, en ignorant la lettre de lecteur ou parties de chemin d’accès UNC/partage de serveur.|  
|[CPathT::StripPath](#strippath)|Appelez cette méthode pour supprimer la partie chemin d’accès d’un chemin d’accès complet et le nom de fichier.|  
|[CPathT::StripToRoot](#striptoroot)|Appelez cette méthode pour supprimer toutes les parties du chemin d’accès à l’exception des informations sur les racine.|  
|[CPathT::UnquoteSpaces](#unquotespaces)|Appelez cette méthode pour supprimer les guillemets au début et la fin d’un chemin d’accès.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[StringType const CPathT::operator se](#operator_const_stringtype_amp)|Cet opérateur permet à l’objet à être traitée comme une chaîne.|  
|[CPathT::operator CPathT::PCXSTR](#operator_cpatht__pcxstr)|Cet opérateur permet à l’objet à être traitée comme une chaîne.|  
|[CPathT::operator StringType se](#operator_stringtype)|Cet opérateur permet à l’objet à être traitée comme une chaîne.|  
|[CPathT::operator +=](#operator_add_eq)|Cet opérateur ajoute une chaîne pour le chemin d’accès.|  
  
### <a name="public-data-members"></a>Membres de données publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CPathT::m_strPath](#m_strpath)|Chemin d’accès.|  
  
## <a name="remarks"></a>Remarques  
 `CPath`, `CPathA`, et `CPathW` sont des instanciations du `CPathT` défini comme suit :  
  
 `typedef CPathT< CString > CPath;`  
  
 `typedef CPathT< CStringA > CPathA;`  
  
 `typedef CPathT< CStringW > CPathW;`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** atlpath.h  
  
##  <a name="addbackslash"></a>CPathT::AddBackslash  
 Appelez cette méthode pour ajouter une barre oblique inverse à la fin d’une chaîne pour créer la syntaxe correcte pour un chemin d’accès. Si le chemin d’accès a déjà une barre oblique, aucune barre oblique inverse ne sera ajoutée.  
  
```
void AddBackslash();
```  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathAddBackSlash](http://msdn.microsoft.com/library/windows/desktop/bb773561).  
  
##  <a name="addextension"></a>CPathT::AddExtension  
 Appelez cette méthode pour ajouter une extension de fichier à un chemin d’accès.  
  
```
BOOL AddExtension(PCXSTR pszExtension);
```  
  
### <a name="parameters"></a>Paramètres  
 `pszExtension`  
 L’extension de fichier à ajouter.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563).  
  
##  <a name="append"></a>CPathT::Append  
 Appelez cette méthode pour ajouter une chaîne pour le chemin d’accès actuel.  
  
```
BOOL Append(PCXSTR pszMore);
```  
  
### <a name="parameters"></a>Paramètres  
 `pszMore`  
 Chaîne à ajouter.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565).  
  
##  <a name="buildroot"></a>CPathT::BuildRoot  
 Appelez cette méthode pour créer un chemin d’accès racine à partir d’un nombre donné de lecteur.  
  
```
void BuildRoot(int iDrive);
```  
  
### <a name="parameters"></a>Paramètres  
 *iDrive*  
 Le numéro du lecteur (0 est a, 1 b et ainsi de suite).  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567).  
  
##  <a name="canonicalize"></a>CPathT::Canonicalize  
 Appelez cette méthode pour convertir le chemin d’accès au format canonique.  
  
```
void Canonicalize();
```  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569).  
  
##  <a name="combine"></a>CPathT::Combine  
 Appelez cette méthode pour concaténer une chaîne représentant un nom de répertoire et une chaîne représentant un nom de chemin d’accès du fichier dans un chemin d’accès.  
  
```
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```  
  
### <a name="parameters"></a>Paramètres  
 `pszDir`  
 Le chemin d’accès du répertoire.  
  
 *pszFile*  
 Le chemin d’accès du fichier.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [PathCombine](http://msdn.microsoft.com/library/windows/desktop/bb773571).  
  
##  <a name="commonprefix"></a>CPathT::CommonPrefix  
 Appelez cette méthode pour déterminer si le chemin d’accès spécifié partage un préfixe commun avec le chemin d’accès actuel.  
  
```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```  
  
### <a name="parameters"></a>Paramètres  
 `pszOther`  
 Le chemin d’accès à comparer à l’objet actuel.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le préfixe commun.  
  
### <a name="remarks"></a>Remarques  
 Un préfixe est un de ces types : « C:\\\\«, ». «, ».. «, ».. \\\\". Pour plus d’informations, consultez [PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574).  
  
##  <a name="compactpath"></a>CPathT::CompactPath  
 Appelez cette méthode pour tronquer un chemin d’accès d’ajuster au sein d’une largeur en pixels donné en remplacement des composants de chemin d’accès avec les points de suspension.  
  
```
BOOL CompactPath(HDC hDC, UINT nWidth);
```  
  
### <a name="parameters"></a>Paramètres  
 `hDC`  
 Le contexte de périphérique utilisé pour les mesures de police.  
  
 `nWidth`  
 La largeur, en pixels, qui sera forcée pour tenir dans la chaîne.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575).  
  
##  <a name="compactpathex"></a>CPathT::CompactPathEx  
 Appelez cette méthode pour tronquer un chemin d’accès à un nombre donné de caractères en remplacement des composants de chemin d’accès avec les points de suspension.  
  
```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```  
  
### <a name="parameters"></a>Paramètres  
 `nMaxChars`  
 Le nombre maximal de caractères devant figurer dans la nouvelle chaîne, y compris le caractère NULL de fin.  
  
 `dwFlags`  
 Réservé.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578).  
  
##  <a name="cpatht"></a>CPathT::CPathT  
 Constructeur.  
  
```
CPathT(PCXSTR pszPath);
CPathT(const CPathT<StringType>& path);
CPathT() throw();
```  
  
### <a name="parameters"></a>Paramètres  
 *pszPath*  
 Pointeur vers une chaîne de chemin d’accès.  
  
 *path*  
 La chaîne de chemin d’accès.  
  
##  <a name="fileexists"></a>CPathT::FileExists  
 Appelez cette méthode pour vérifier si le fichier à ce nom de chemin d’accès existe.  
  
```
BOOL FileExists() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE si le fichier existe, FALSE dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584).  
  
##  <a name="findextension"></a>CPathT::FindExtension  
 Appelez cette méthode pour rechercher la position de l’extension de fichier dans le chemin d’accès.  
  
```
int FindExtension() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la position de la «. » qui précède l’extension. Si aucune extension n’est trouvée, retourne -1.  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587).  
  
##  <a name="findfilename"></a>CPathT::FindFileName  
 Appelez cette méthode pour trouver la position du nom de fichier dans le chemin d’accès.  
  
```
int FindFileName() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la position du nom de fichier. Si aucun nom de fichier n’est trouvé, retourne -1.  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589).  
  
##  <a name="getdrivenumber"></a>CPathT::GetDriveNumber  
 Appelez cette méthode pour rechercher le chemin d’accès pour une lettre de lecteur dans la plage de 'A' à 'Z' et retourner le nombre de lecteur correspondant.  
  
```
int GetDriveNumber() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le nombre de lecteur sous forme d’entier compris entre 0 et 25 (correspondant à 'A' à 'Z') si le chemin d’accès comporte une lettre de lecteur, ou -1 dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612).  
  
##  <a name="getextension"></a>CPathT::GetExtension  
 Appelez cette méthode pour obtenir l’extension de fichier dans le chemin d’accès.  
  
```
StringType GetExtension() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne l’extension de fichier.  
  
##  <a name="isdirectory"></a>CPathT::IsDirectory  
 Appelez cette méthode pour vérifier si le chemin d’accès est un répertoire valide.  
  
```
BOOL IsDirectory() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une valeur différente de zéro (16) si le chemin d’accès est un répertoire, `FALSE` dans le cas contraire.  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathIsDirectory](http://msdn.microsoft.com/library/windows/desktop/bb773621).  
  
##  <a name="isfilespec"></a>CPathT::IsFileSpec  
 Appelez cette méthode pour rechercher un chemin d’accès pour tous les caractères de délimitation de chemin d’accès (par exemple, ' :' ou '\\'). S’il n’y a aucun caractère délimiteur de chemin d’accès existe, le chemin d’accès est considéré comme un chemin d’accès de la spécification de fichier.  
  
```
BOOL IsFileSpec() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne TRUE si aucun caractère délimiteur de chemin d’accès dans le chemin d’accès, ou FALSE s’il existe des caractères de délimitation de chemin d’accès.  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627).  
  
##  <a name="isprefix"></a>CPathT::IsPrefix  
 Appelez cette méthode pour déterminer si un chemin d’accès contient un préfixe valide du type passé `pszPrefix`.  
  
```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `pszPrefix`  
 Préfixe à rechercher. Un préfixe est un de ces types : « C:\\\\«, ». «, ».. «, ».. \\\\".  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne TRUE si le chemin d’accès contient un préfixe, ou FALSE dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650).  
  
##  <a name="isrelative"></a>CPathT::IsRelative  
 Appelez cette méthode pour déterminer si le chemin d’accès est relatif.  
  
```
BOOL IsRelative() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Renvoie TRUE si le chemin d’accès est relatif, ou FALSE si elle est absolue.  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660).  
  
##  <a name="isroot"></a>CPathT::IsRoot  
 Appelez cette méthode pour déterminer si le chemin d’accès est un répertoire racine.  
  
```
BOOL IsRoot() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne TRUE si le chemin d’accès est une racine, ou FALSE dans le cas contraire.  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674).  
  
##  <a name="issameroot"></a>CPathT::IsSameRoot  
 Appelez cette méthode pour déterminer si un autre chemin d’accès est un composant racine commun avec le chemin d’accès actuel.  
  
```
BOOL IsSameRoot(PCXSTR pszOther) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `pszOther`  
 L’autre tracé.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne TRUE si les deux chaînes ont le même composant racine, ou FALSE dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687).  
  
##  <a name="isunc"></a>CPathT::IsUNC  
 Appelez cette méthode pour déterminer si le chemin d’accès est un chemin d’accès UNC (convention de dénomination universelle) valide pour un serveur et partager.  
  
```
BOOL IsUNC() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Renvoie TRUE si le chemin d’accès est un chemin UNC valide, ou FALSE dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712).  
  
##  <a name="isuncserver"></a>CPathT::IsUNCServer  
 Appelez cette méthode pour déterminer si le chemin d’accès est un chemin d’accès UNC (convention de dénomination universelle) valide pour un seul serveur.  
  
```
BOOL IsUNCServer() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE si la chaîne est un chemin d’accès UNC pour un seul serveur (aucun nom de partage) valide, ou FALSE dans le cas contraire.  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722).  
  
##  <a name="isuncservershare"></a>CPathT::IsUNCServerShare  
 Appelez cette méthode pour déterminer si le chemin d’accès est un chemin de partage UNC (convention de dénomination universelle) valid, \\ \  *server*\ *partager*.  
  
```
BOOL IsUNCServerShare() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne TRUE si le chemin d’accès est sous la forme \\ \  *server*\ *partager*, ou FALSE dans le cas contraire.  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723).  
  
##  <a name="m_strpath"></a>CPathT::m_strPath  
 Chemin d’accès.  
  
```
StringType m_strPath;
```  
  
### <a name="remarks"></a>Notes  
 `StringType`est le paramètre de modèle `CPathT`.  
  
##  <a name="makepretty"></a>CPathT::MakePretty  
 Appelez cette méthode pour convertir un chemin d’accès à tous les caractères en minuscules pour donner le chemin d’accès une apparence cohérente.  
  
```
BOOL MakePretty();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne TRUE si le chemin d’accès a été convertie, ou FALSE dans le cas contraire.  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725).  
  
##  <a name="matchspec"></a>CPathT::MatchSpec  
 Appelez cette méthode pour rechercher le chemin d’accès d’une chaîne contenant un type de correspondance de caractère générique.  
  
```
BOOL MatchSpec(PCXSTR pszSpec) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `pszSpec`  
 Pointeur vers une chaîne terminée par null avec le type de fichier à rechercher. Par exemple, pour vérifier si le fichier dans le chemin d’accès actuel est un fichier DOC, `pszSpec` doit être définie sur « * .doc ».  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne si la chaîne correspond à la valeur TRUE ou FALSE dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727).  
  
##  <a name="operator_add_eq"></a>CPathT::operator +=  
 Cet opérateur ajoute une chaîne pour le chemin d’accès.  
  
```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```  
  
### <a name="parameters"></a>Paramètres  
 `pszMore`  
 Chaîne à ajouter.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne le chemin d’accès de mise à jour.  
  
##  <a name="operator_const_stringtype_amp"></a>StringType const CPathT::operator&amp;  
 Cet opérateur permet à l’objet à être traitée comme une chaîne.  
  
```
 operatorconst StringType&() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une chaîne représentant le chemin d’accès actuel géré par cet objet.  
  
##  <a name="operator_cpatht__pcxstr"></a>CPathT::operator CPathT::PCXSTR  
 Cet opérateur permet à l’objet à être traitée comme une chaîne.  
  
```
 operatorPCXSTR() const throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une chaîne représentant le chemin d’accès actuel géré par cet objet.  
  
##  <a name="operator_stringtype__amp"></a>CPathT::operator StringType&amp;  
 Cet opérateur permet à l’objet à être traitée comme une chaîne.  
  
```
 operatorStringType&() throw();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne une chaîne représentant le chemin d’accès actuel géré par cet objet.  
  
##  <a name="pcxstr"></a>CPathT::PCXSTR  
 Un type de chaîne constante.  
  
```
typedef StringType::PCXSTR PCXSTR;
```  
  
### <a name="remarks"></a>Remarques  
 `StringType`est le paramètre de modèle `CPathT`.  
  
##  <a name="pxstr"></a>CPathT::PXSTR  
 Un type string.  
  
```
typedef StringType::PXSTR PXSTR;
```  
  
### <a name="remarks"></a>Remarques  
 `StringType`est le paramètre de modèle `CPathT`.  
  
##  <a name="quotespaces"></a>CPathT::QuoteSpaces  
 Appelez cette méthode pour délimiter le chemin d’accès entre guillemets si elle contient des espaces.  
  
```
void QuoteSpaces();
```  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739).  
  
##  <a name="relativepathto"></a>CPathT::RelativePathTo  
 Appelez cette méthode pour créer un chemin d’accès relatif à partir d’un fichier ou dossier à un autre.  
  
```
BOOL RelativePathTo(
    PCXSTR pszFrom,
    DWORD dwAttrFrom,
    PCXSTR pszTo,
    DWORD dwAttrTo);
```  
  
### <a name="parameters"></a>Paramètres  
 `pszFrom`  
 Début du chemin d’accès relatif.  
  
 *dwAttrFrom*  
 Les attributs du fichier de `pszFrom`. Si cette valeur contient FILE_ATTRIBUTE_DIRECTORY, `pszFrom` est supposé être un répertoire ; sinon, `pszFrom` est supposé pour être un fichier.  
  
 `pszTo`  
 Le point de terminaison du chemin d’accès relatif.  
  
 *dwAttrTo*  
 Les attributs du fichier de `pszTo`. Si cette valeur contient FILE_ATTRIBUTE_DIRECTORY, `pszTo` est supposé être un répertoire ; sinon, `pszTo` est supposé pour être un fichier.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740).  
  
##  <a name="removeargs"></a>CPathT::RemoveArgs  
 Appelez cette méthode pour supprimer tous les arguments de ligne de commande du chemin d’accès.  
  
```
void RemoveArgs();
```  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742).  
  
##  <a name="removebackslash"></a>CPathT::RemoveBackslash  
 Appelez cette méthode pour supprimer de la barre oblique de fin du chemin d’accès.  
  
```
void RemoveBackslash();
```  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743).  
  
##  <a name="removeblanks"></a>CPathT::RemoveBlanks  
 Appelez cette méthode pour supprimer tous les espaces de début et de fin du chemin d’accès.  
  
```
void RemoveBlanks();
```  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745).  
  
##  <a name="removeextension"></a>CPathT::RemoveExtension  
 Appelez cette méthode pour supprimer l’extension de fichier du chemin d’accès, le cas échéant.  
  
```
void RemoveExtension();
```  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746).  
  
##  <a name="removefilespec"></a>CPathT::RemoveFileSpec  
 Appelez cette méthode pour supprimer le chemin d’accès, le nom du fichier à droite et la barre oblique inverse si elle possède les.  
  
```
BOOL RemoveFileSpec();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748).  
  
##  <a name="renameextension"></a>CPathT::RenameExtension  
 Appelez cette méthode pour remplacer l’extension de nom de fichier dans le chemin d’accès avec une nouvelle extension. Si le nom de fichier ne contient pas une extension, l’extension est attachée à la fin du chemin d’accès.  
  
```
BOOL RenameExtension(PCXSTR pszExtension);
```  
  
### <a name="parameters"></a>Paramètres  
 `pszExtension`  
 La nouvelle extension de nom de fichier, précédé par un «. » caractères.  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la valeur TRUE en cas de réussite, FALSE en cas d’échec.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749).  
  
##  <a name="skiproot"></a>CPathT::SkipRoot  
 Appelez cette méthode pour analyser un chemin d’accès, en ignorant la lettre de lecteur ou parties de chemin d’accès UNC (convention de dénomination universelle) / partage de serveur.  
  
```
int SkipRoot() const;
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne la position de début de la sous-chemin qui suit la racine (lettre de lecteur ou partage de serveur/UNC).  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754).  
  
##  <a name="strippath"></a>CPathT::StripPath  
 Appelez cette méthode pour supprimer la partie chemin d’accès d’un chemin d’accès complet et le nom de fichier.  
  
```
void StripPath();
```  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756).  
  
##  <a name="striptoroot"></a>CPathT::StripToRoot  
 Appelez cette méthode pour supprimer toutes les parties du chemin d’accès à l’exception des informations sur les racine.  
  
```
BOOL StripToRoot();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne TRUE si une lettre de lecteur valide a été trouvé dans le chemin d’accès, ou FALSE dans le cas contraire.  
  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757).  
  
##  <a name="unquotespaces"></a>CPathT::UnquoteSpaces  
 Appelez cette méthode pour supprimer les guillemets au début et la fin d’un chemin d’accès.  
  
```
void UnquoteSpaces();
```  
  
### <a name="remarks"></a>Remarques  
 Pour plus d’informations, consultez [PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763).  
  
##  <a name="xchar"></a>CPathT::XCHAR  
 Type de caractère.  
  
```
typedef StringType::XCHAR XCHAR;
```  
  
### <a name="remarks"></a>Notes  
 `StringType`est le paramètre de modèle `CPathT`.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../atl/reference/atl-classes.md)   
 [CStringT (classe)](../../atl-mfc-shared/reference/cstringt-class.md)
