---
title: Référence des utilitaires ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: dd8a2888-34f4-461e-9bf4-834218f9b95b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d11e06b7a8b8bc636de906a210cfffb62c6eeff4
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220318"
---
# <a name="atl-utilities-reference"></a>Référence des utilitaires ATL
ATL fournit le code permettant de manipuler des URL et les chemins d’accès sous la forme de [CPathT](../atl/reference/cpatht-class.md) et [CUrl](../atl/reference/curl-class.md). Un pool de threads, [CThreadPool](../atl/reference/cthreadpool-class.md), peut être utilisé dans vos applications. Vous trouverez ce code dans atlpath.h et atlutil.h.  
  
### <a name="classes"></a>Classes  
  
|||  
|-|-|  
|[CPathT, classe](../atl/reference/cpatht-class.md)|Cette classe représente un chemin d’accès.|  
|[CDebugReportHook, classe](../atl/reference/cdebugreporthook-class.md)|Utilisez cette classe pour envoyer des rapports de débogage à un canal nommé.|  
|[CNonStatelessWorker, classe](../atl/reference/cnonstatelessworker-class.md)|Reçoit des demandes à partir d’un pool de threads et les transmet à un objet de travail qui est créé et détruit dans chaque demande.|  
|[CNoWorkerThread, classe](../atl/reference/cnoworkerthread-class.md)|Utilisez cette classe comme argument pour le `MonitorClass` paramètre de modèle pour les classes de cache si vous souhaitez désactiver la maintenance du cache dynamique.|  
|[CThreadPool, classe](../atl/reference/cthreadpool-class.md)|Cette classe fournit un pool de threads de travail qui traitent une file d’attente d’éléments de travail.|  
|[CUrl, classe](../atl/reference/curl-class.md)|Cette classe représente une URL. Il vous permet de manipuler chaque élément de l’URL indépendamment des autres si l’analyse une URL existante de chaîne ou de création d’une chaîne à partir de zéro.|  
|[CWorkerThread, classe](../atl/reference/cworkerthread-class.md)|Cette classe crée un thread de travail ou utilise un, attend sur un ou plusieurs handles d’objet de noyau et exécute une fonction cliente spécifiée lorsqu’une des poignées est signalée.|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[CPath](../atl/reference/atl-typedefs.md#cpath)|Une spécialisation de [CPathT](../atl/reference/cpatht-class.md) à l’aide de `CString`.|  
|[CPathA](../atl/reference/atl-typedefs.md#cpatha)|Une spécialisation de [CPathT](../atl/reference/cpatht-class.md) à l’aide de `CStringA`.|  
|[CPathW](../atl/reference/atl-typedefs.md#cpathw)|Une spécialisation de [CPathT](../atl/reference/cpatht-class.md) à l’aide de `CStringW`.|  
|[ATL_URL_PORT](../atl/reference/atl-typedefs.md#atl_url_port)|Le type utilisé par [CUrl](../atl/reference/curl-class.md) pour spécifier un numéro de port.|  
  
### <a name="enums"></a>Enums  
  
|||  
|-|-|  
|[ATL_URL_SCHEME](../atl/reference/atl-url-scheme-enum.md)|Les membres de cette énumération fournissent des constantes pour les schémas compris par [CUrl](../atl/reference/curl-class.md).|  
  
### <a name="functions"></a>Fonctions  
  
|||  
|-|-|  
|[AtlCanonicalizeUrl](../atl/reference/atl-http-utility-functions.md#atlcanonicalizeurl)|Appelez cette fonction pour rendre canonique une URL, notamment afin de convertir les caractères et espaces non sécurisés en séquences d'échappement.|  
|[AtlCombineUrl](../atl/reference/atl-http-utility-functions.md#atlcombineurl)|Appelez cette fonction pour associer une URL de base et une URL relative en une URL unique et canonique.|  
|[AtlEscapeUrl](../atl/reference/atl-http-utility-functions.md#atlescapeurl)|Appelez cette fonction pour convertir tous les caractères non sécurisés en séquences d'échappement.|  
|[AtlGetDefaultUrlPort](../atl/reference/atl-http-utility-functions.md#atlgetdefaulturlport)|Appelez cette fonction pour obtenir le numéro de port par défaut associé à un protocole internet particulier ou d’un schéma.|  
|[AtlHexValue](../atl/reference/atl-text-encoding-functions.md#atlhexvalue)|Appelez cette fonction pour obtenir la valeur numérique d'un chiffre hexadécimal.|  
|[AtlIsUnsafeUrlChar](../atl/reference/atl-http-utility-functions.md#atlisunsafeurlchar)|Appelez cette fonction pour déterminer si un caractère peut être utilisé de manière sécurisée dans une URL.|  
|[AtlUnescapeUrl](../atl/reference/atl-http-utility-functions.md#atlunescapeurl)|Appelez cette fonction pour convertir les caractères ayant fait l'objet d'une séquence d'échappement vers leurs valeurs d'origine.|  
|[SystemTimeToHttpDate](../atl/reference/atl-http-utility-functions.md#systemtimetohttpdate)|Appelez cette fonction pour convertir une heure système en une chaîne au format approprié pour être utilisée dans les en-têtes HTTP.|  

|[ATLPath::AddBackslash](../atl/reference/atl-path-functions.md#addbackslash)| Cette fonction est un wrapper surchargé de [PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha
). |  
|[ATLPath::AddExtension](../atl/reference/atl-path-functions.md#addextension)| Cette fonction est un wrapper surchargé de [PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona). |  
|[ATLPath::Append](../atl/reference/atl-path-functions.md#append)| Cette fonction est un wrapper surchargé de [PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda). |  
|[ATLPath::BuildRoot](../atl/reference/atl-path-functions.md#buildroot)| Cette fonction est un wrapper surchargé de [PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota). |  
|[ATLPath::Canonicalize](../atl/reference/atl-path-functions.md#canonicalize)| Cette fonction est un wrapper surchargé de [PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea). |  
|[ATLPath::Combine](../atl/reference/atl-path-functions.md#combine)| Cette fonction est un wrapper surchargé de [PathCombine](/windows/desktop/api/shlwapi/nf-shlwapi-pathcombinea). |  
|[ATLPath::CommonPrefix](../atl/reference/atl-path-functions.md#commonprefix)| Cette fonction est un wrapper surchargé de [PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa). |  
|[ATLPath::CompactPath](../atl/reference/atl-path-functions.md#compactpath)| Cette fonction est un wrapper surchargé de [PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha). |  
|[ATLPath::CompactPathEx](../atl/reference/atl-path-functions.md#compactpathex)| Cette fonction est un wrapper surchargé de [PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa). |  
|[ATLPath::FileExists](../atl/reference/atl-path-functions.md#fileexists)| Cette fonction est un wrapper surchargé de [PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa). |  
|[ATLPath::FindExtension](../atl/reference/atl-path-functions.md#findextension)| Cette fonction est un wrapper surchargé de [PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona). |  
|[ATLPath::FindFileName](../atl/reference/atl-path-functions.md#findfilename)| Cette fonction est un wrapper surchargé de [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea). |  
|[ATLPath::GetDriveNumber](../atl/reference/atl-path-functions.md#getdrivenumber)| Cette fonction est un wrapper surchargé de [PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera). |  
|[ATLPath::IsDirectory](../atl/reference/atl-path-functions.md#isdirectory)| Cette fonction est un wrapper surchargé de [PathIsDirectory](/windows/desktop/api/shlwapi/nf-shlwapi-pathisdirectorya). |  
|[ATLPath::IsFileSpec](../atl/reference/atl-path-functions.md#isfilespec)| Cette fonction est un wrapper surchargé de [PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca). |  
|[ATLPath::IsPrefix](../atl/reference/atl-path-functions.md#isprefix)| Cette fonction est un wrapper surchargé de [PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa). |  
|[ATLPath::IsRelative](../atl/reference/atl-path-functions.md#isrelative)| Cette fonction est un wrapper surchargé de [PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea). |  
|[ATLPath::IsRoot](../atl/reference/atl-path-functions.md#isroot)| Cette fonction est un wrapper surchargé de [PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota). |  
|[ATLPath::IsSameRoot](../atl/reference/atl-path-functions.md#issameroot)| Cette fonction est un wrapper surchargé de [PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota). |  
|[ATLPath::IsUNC](../atl/reference/atl-path-functions.md#isunc)| Cette fonction est un wrapper surchargé de [PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca). |  
|[ATLPath::IsUNCServer](../atl/reference/atl-path-functions.md#isuncserver)| Cette fonction est un wrapper surchargé de [PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera). |  
|[ATLPath::IsUNCServerShare](../atl/reference/atl-path-functions.md#isuncservershare)| Cette fonction est un wrapper surchargé de [PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea). |  
|[ATLPath::MakePretty](../atl/reference/atl-path-functions.md#makepretty)| Cette fonction est un wrapper surchargé de [PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya). |  
|[ATLPath::MatchSpec](../atl/reference/atl-path-functions.md#matchspec)| Cette fonction est un wrapper surchargé de [PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca). |  
|[ATLPath::QuoteSpaces](../atl/reference/atl-path-functions.md#quotespaces)| Cette fonction est un wrapper surchargé de [PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa). |  
|[ATLPath::RelativePathTo](../atl/reference/atl-path-functions.md#relativepathto)| Cette fonction est un wrapper surchargé de [PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa). |  
|[ATLPath::RemoveArgs](../atl/reference/atl-path-functions.md#removeargs)| Cette fonction est un wrapper surchargé de [PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa). |  
|[ATLPath::RemoveBackslash](../atl/reference/atl-path-functions.md#removebackslash)| Cette fonction est un wrapper surchargé de [PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha). |  
|[ATLPath::RemoveBlanks](../atl/reference/atl-path-functions.md#removeblanks)| Cette fonction est un wrapper surchargé de [PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa). |  
|[ATLPath::RemoveExtension](../atl/reference/atl-path-functions.md#removeextension)| Cette fonction est un wrapper surchargé de [PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona). |  
|[ATLPath::RemoveFileSpec](../atl/reference/atl-path-functions.md#removefilespec)| Cette fonction est un wrapper surchargé de [PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca). |  
|[ATLPath::RenameExtension](../atl/reference/atl-path-functions.md#renameextension)| Cette fonction est un wrapper surchargé de [PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona). |  
|[ATLPath::SkipRoot](../atl/reference/atl-path-functions.md#skiproot)| Cette fonction est un wrapper surchargé de [PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota). |  
|[ATLPath::StripPath](../atl/reference/atl-path-functions.md#strippath)| Cette fonction est un wrapper surchargé de [PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha). |  
|[ATLPath::StripToRoot](../atl/reference/atl-path-functions.md#striptoroot)| Cette fonction est un wrapper surchargé de [PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota). |  
|[ATLPath::UnquoteSpaces](../atl/reference/atl-path-functions.md#unquotespaces)| Cette fonction est un wrapper surchargé de [PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa). |  
  

## <a name="see-also"></a>Voir aussi  
 [Concepts](../atl/active-template-library-atl-concepts.md)   
 [Composants de bureau COM ATL](../atl/atl-com-desktop-components.md)
