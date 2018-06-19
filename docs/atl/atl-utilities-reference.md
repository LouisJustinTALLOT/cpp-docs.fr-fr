---
title: Référence des utilitaires ATL | Documents Microsoft
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
ms.openlocfilehash: 9b802d8764dda321e2e313f793f4f2e4745dbcc7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363821"
---
# <a name="atl-utilities-reference"></a>Référence des utilitaires ATL
ATL fournit du code pour la manipulation d’URL et les chemins d’accès sous la forme de [CPathT](../atl/reference/cpatht-class.md) et [CUrl](../atl/reference/curl-class.md). Un pool de threads, [CThreadPool](../atl/reference/cthreadpool-class.md), peut être utilisé dans vos applications. Vous trouverez ce code dans atlpath.h et atlutil.h.  
  
### <a name="classes"></a>Classes  
  
|||  
|-|-|  
|[CPathT, classe](../atl/reference/cpatht-class.md)|Cette classe représente un chemin d’accès.|  
|[CDebugReportHook, classe](../atl/reference/cdebugreporthook-class.md)|Cette classe permet d’envoyer des rapports de débogage à un canal nommé.|  
|[CNonStatelessWorker, classe](../atl/reference/cnonstatelessworker-class.md)|Reçoit des demandes à partir d’un pool de threads et les transmet à un objet de travail qui est créé et détruit à chaque demande.|  
|[CNoWorkerThread, classe](../atl/reference/cnoworkerthread-class.md)|Utilisez cette classe comme argument pour le `MonitorClass` paramètre de modèle pour les classes de cache si vous souhaitez désactiver la maintenance du cache dynamique.|  
|[CThreadPool, classe](../atl/reference/cthreadpool-class.md)|Cette classe fournit un pool de threads de travail qui traitent d’une file d’attente d’éléments de travail.|  
|[CUrl, classe](../atl/reference/curl-class.md)|Cette classe représente une URL. Il vous permet de manipuler chaque élément de l’URL indépendamment des autres si l’analyse des URL existante de chaîne ou de génération d’une chaîne à partir de zéro.|  
|[CWorkerThread, classe](../atl/reference/cworkerthread-class.md)|Cette classe crée un thread de travail ou utilise un existant, attend sur un ou plusieurs handles d’objet noyau et exécute une fonction de client spécifié lors d’une des poignées est signalée.|  
  
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
|[AtlGetDefaultUrlPort](../atl/reference/atl-http-utility-functions.md#atlgetdefaulturlport)|Appelez cette fonction pour obtenir le numéro de port par défaut associé à un protocole internet ou le schéma.|  
|[AtlHexValue](../atl/reference/atl-text-encoding-functions.md#atlhexvalue)|Appelez cette fonction pour obtenir la valeur numérique d'un chiffre hexadécimal.|  
|[AtlIsUnsafeUrlChar](../atl/reference/atl-http-utility-functions.md#atlisunsafeurlchar)|Appelez cette fonction pour déterminer si un caractère peut être utilisé de manière sécurisée dans une URL.|  
|[AtlUnescapeUrl](../atl/reference/atl-http-utility-functions.md#atlunescapeurl)|Appelez cette fonction pour convertir les caractères ayant fait l'objet d'une séquence d'échappement vers leurs valeurs d'origine.|  
|[SystemTimeToHttpDate](../atl/reference/atl-http-utility-functions.md#systemtimetohttpdate)|Appelez cette fonction pour convertir une heure système en une chaîne au format approprié pour être utilisée dans les en-têtes HTTP.|  

|[ATLPath::AddBackslash](../atl/reference/atl-path-functions.md#addbackslash)| Cette fonction est un wrapper surchargé de [PathAddBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773561). |  
|[ATLPath::AddExtension](../atl/reference/atl-path-functions.md#addextension)| Cette fonction est un wrapper surchargé de [PathAddExtension](http://msdn.microsoft.com/library/windows/desktop/bb773563). |  
|[ATLPath::Append](../atl/reference/atl-path-functions.md#append)| Cette fonction est un wrapper surchargé de [PathAppend](http://msdn.microsoft.com/library/windows/desktop/bb773565). |  
|[ATLPath::BuildRoot](../atl/reference/atl-path-functions.md#buildroot)| Cette fonction est un wrapper surchargé de [PathBuildRoot](http://msdn.microsoft.com/library/windows/desktop/bb773567). |  
|[ATLPath::Canonicalize](../atl/reference/atl-path-functions.md#canonicalize)| Cette fonction est un wrapper surchargé de [PathCanonicalize](http://msdn.microsoft.com/library/windows/desktop/bb773569). |  
|[ATLPath::Combine](../atl/reference/atl-path-functions.md#combine)| Cette fonction est un wrapper surchargé de [PathCombine](http://msdn.microsoft.com/library/windows/desktop/bb773571). |  
|[ATLPath::CommonPrefix](../atl/reference/atl-path-functions.md#commonprefix)| Cette fonction est un wrapper surchargé de [PathCommonPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773574). |  
|[ATLPath::CompactPath](../atl/reference/atl-path-functions.md#compactpath)| Cette fonction est un wrapper surchargé de [PathCompactPath](http://msdn.microsoft.com/library/windows/desktop/bb773575). |  
|[ATLPath::CompactPathEx](../atl/reference/atl-path-functions.md#compactpathex)| Cette fonction est un wrapper surchargé de [PathCompactPathEx](http://msdn.microsoft.com/library/windows/desktop/bb773578). |  
|[ATLPath::FileExists](../atl/reference/atl-path-functions.md#fileexists)| Cette fonction est un wrapper surchargé de [PathFileExists](http://msdn.microsoft.com/library/windows/desktop/bb773584). |  
|[ATLPath::FindExtension](../atl/reference/atl-path-functions.md#findextension)| Cette fonction est un wrapper surchargé de [PathFindExtension](http://msdn.microsoft.com/library/windows/desktop/bb773587). |  
|[ATLPath::FindFileName](../atl/reference/atl-path-functions.md#findfilename)| Cette fonction est un wrapper surchargé de [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589). |  
|[ATLPath::GetDriveNumber](../atl/reference/atl-path-functions.md#getdrivenumber)| Cette fonction est un wrapper surchargé de [PathGetDriveNumber](http://msdn.microsoft.com/library/windows/desktop/bb773612). |  
|[ATLPath::IsDirectory](../atl/reference/atl-path-functions.md#isdirectory)| Cette fonction est un wrapper surchargé de [PathIsDirectory](http://msdn.microsoft.com/library/windows/desktop/bb773621). |  
|[ATLPath::IsFileSpec](../atl/reference/atl-path-functions.md#isfilespec)| Cette fonction est un wrapper surchargé de [PathIsFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773627). |  
|[ATLPath::IsPrefix](../atl/reference/atl-path-functions.md#isprefix)| Cette fonction est un wrapper surchargé de [PathIsPrefix](http://msdn.microsoft.com/library/windows/desktop/bb773650). |  
|[ATLPath::IsRelative](../atl/reference/atl-path-functions.md#isrelative)| Cette fonction est un wrapper surchargé de [PathIsRelative](http://msdn.microsoft.com/library/windows/desktop/bb773660). |  
|[ATLPath::IsRoot](../atl/reference/atl-path-functions.md#isroot)| Cette fonction est un wrapper surchargé de [PathIsRoot](http://msdn.microsoft.com/library/windows/desktop/bb773674). |  
|[ATLPath::IsSameRoot](../atl/reference/atl-path-functions.md#issameroot)| Cette fonction est un wrapper surchargé de [PathIsSameRoot](http://msdn.microsoft.com/library/windows/desktop/bb773687). |  
|[ATLPath::IsUNC](../atl/reference/atl-path-functions.md#isunc)| Cette fonction est un wrapper surchargé de [PathIsUNC](http://msdn.microsoft.com/library/windows/desktop/bb773712). |  
|[ATLPath::IsUNCServer](../atl/reference/atl-path-functions.md#isuncserver)| Cette fonction est un wrapper surchargé de [PathIsUNCServer](http://msdn.microsoft.com/library/windows/desktop/bb773722). |  
|[ATLPath::IsUNCServerShare](../atl/reference/atl-path-functions.md#isuncservershare)| Cette fonction est un wrapper surchargé de [PathIsUNCServerShare](http://msdn.microsoft.com/library/windows/desktop/bb773723). |  
|[ATLPath::MakePretty](../atl/reference/atl-path-functions.md#makepretty)| Cette fonction est un wrapper surchargé de [PathMakePretty](http://msdn.microsoft.com/library/windows/desktop/bb773725). |  
|[ATLPath::MatchSpec](../atl/reference/atl-path-functions.md#matchspec)| Cette fonction est un wrapper surchargé de [PathMatchSpec](http://msdn.microsoft.com/library/windows/desktop/bb773727). |  
|[ATLPath::QuoteSpaces](../atl/reference/atl-path-functions.md#quotespaces)| Cette fonction est un wrapper surchargé de [PathQuoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773739). |  
|[ATLPath::RelativePathTo](../atl/reference/atl-path-functions.md#relativepathto)| Cette fonction est un wrapper surchargé de [PathRelativePathTo](http://msdn.microsoft.com/library/windows/desktop/bb773740). |  
|[ATLPath::RemoveArgs](../atl/reference/atl-path-functions.md#removeargs)| Cette fonction est un wrapper surchargé de [PathRemoveArgs](http://msdn.microsoft.com/library/windows/desktop/bb773742). |  
|[ATLPath::RemoveBackslash](../atl/reference/atl-path-functions.md#removebackslash)| Cette fonction est un wrapper surchargé de [PathRemoveBackslash](http://msdn.microsoft.com/library/windows/desktop/bb773743). |  
|[ATLPath::RemoveBlanks](../atl/reference/atl-path-functions.md#removeblanks)| Cette fonction est un wrapper surchargé de [PathRemoveBlanks](http://msdn.microsoft.com/library/windows/desktop/bb773745). |  
|[ATLPath::RemoveExtension](../atl/reference/atl-path-functions.md#removeextension)| Cette fonction est un wrapper surchargé de [PathRemoveExtension](http://msdn.microsoft.com/library/windows/desktop/bb773746). |  
|[ATLPath::RemoveFileSpec](../atl/reference/atl-path-functions.md#removefilespec)| Cette fonction est un wrapper surchargé de [PathRemoveFileSpec](http://msdn.microsoft.com/library/windows/desktop/bb773748). |  
|[ATLPath::RenameExtension](../atl/reference/atl-path-functions.md#renameextension)| Cette fonction est un wrapper surchargé de [PathRenameExtension](http://msdn.microsoft.com/library/windows/desktop/bb773749). |  
|[ATLPath::SkipRoot](../atl/reference/atl-path-functions.md#skiproot)| Cette fonction est un wrapper surchargé de [PathSkipRoot](http://msdn.microsoft.com/library/windows/desktop/bb773754). |  
|[ATLPath::StripPath](../atl/reference/atl-path-functions.md#strippath)| Cette fonction est un wrapper surchargé de [PathStripPath](http://msdn.microsoft.com/library/windows/desktop/bb773756). |  
|[ATLPath::StripToRoot](../atl/reference/atl-path-functions.md#striptoroot)| Cette fonction est un wrapper surchargé de [PathStripToRoot](http://msdn.microsoft.com/library/windows/desktop/bb773757). |  
|[ATLPath::UnquoteSpaces](../atl/reference/atl-path-functions.md#unquotespaces)| Cette fonction est un wrapper surchargé de [PathUnquoteSpaces](http://msdn.microsoft.com/library/windows/desktop/bb773763). |  
  

## <a name="see-also"></a>Voir aussi  
 [Concepts](../atl/active-template-library-atl-concepts.md)   
 [Composants de bureau COM ATL](../atl/atl-com-desktop-components.md)
