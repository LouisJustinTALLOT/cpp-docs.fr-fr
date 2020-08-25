---
title: Référence des utilitaires ATL
ms.date: 11/04/2016
ms.assetid: dd8a2888-34f4-461e-9bf4-834218f9b95b
ms.openlocfilehash: f9e59a2c67d391995d94d77f526613534acb48de
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831873"
---
# <a name="atl-utilities-reference"></a>Référence des utilitaires ATL

ATL fournit du code pour manipuler les chemins d’accès et les URL sous la forme de [CPathT](../atl/reference/cpatht-class.md) et de la [boucle](../atl/reference/curl-class.md). Un pool de threads, [CThreadPool](../atl/reference/cthreadpool-class.md), peut être utilisé dans vos applications. Vous trouverez ce code dans atlpath.h et atlutil.h.

## <a name="classes"></a>Classes

| &nbsp; | &nbsp; |
|--|--|
| [CPathT, classe](../atl/reference/cpatht-class.md) | Cette classe représente un chemin d’accès. |
| [CDebugReportHook, classe](../atl/reference/cdebugreporthook-class.md) | Utilisez cette classe pour envoyer des rapports de débogage à un canal nommé. |
| [CNonStatelessWorker, classe](../atl/reference/cnonstatelessworker-class.md) | Reçoit des demandes d’un pool de threads et les passe à un objet de travail créé et détruit à chaque requête. |
| [CNoWorkerThread, classe](../atl/reference/cnoworkerthread-class.md) | Utilisez cette classe comme argument pour le `MonitorClass` paramètre de modèle pour mettre en cache des classes si vous souhaitez désactiver la maintenance de cache dynamique. |
| [CThreadPool, classe](../atl/reference/cthreadpool-class.md) | Cette classe fournit un pool de threads de travail qui traitent une file d’attente d’éléments de travail. |
| [CUrl, classe](../atl/reference/curl-class.md) | Cette classe représente une URL. Elle vous permet de manipuler chaque élément de l’URL indépendamment des autres, si l’analyse d’une chaîne d’URL existante ou la génération d’une chaîne à partir de zéro. |
| [CWorkerThread, classe](../atl/reference/cworkerthread-class.md) | Cette classe crée un thread de travail ou en utilise un, attend un ou plusieurs handles d’objet de noyau et exécute une fonction cliente spécifiée lorsque l’un des descripteurs est signalé. |

## <a name="typedefs"></a>Typedefs

| &emsp; | &emsp; |
|--|--|
| [CPath](../atl/reference/atl-typedefs.md#cpath) | Une spécialisation de [CPathT](../atl/reference/cpatht-class.md) à l’aide de `CString` . |
| [CPathA](../atl/reference/atl-typedefs.md#cpatha) | Une spécialisation de [CPathT](../atl/reference/cpatht-class.md) à l’aide de `CStringA` . |
| [CPathW](../atl/reference/atl-typedefs.md#cpathw) | Une spécialisation de [CPathT](../atl/reference/cpatht-class.md) à l’aide de `CStringW` . |
| [ATL_URL_PORT](../atl/reference/atl-typedefs.md#atl_url_port) | Type utilisé par la [boucle](../atl/reference/curl-class.md) pour spécifier un numéro de port. |

## <a name="enums"></a>Énumérations

| &emsp; | &emsp; |
|--|--|
| [ATL_URL_SCHEME](../atl/reference/atl-url-scheme-enum.md) | Les membres de cette énumération fournissent des constantes pour les schémas comprises par la [boucle](../atl/reference/curl-class.md). |

## <a name="functions"></a>Functions

| &emsp; | &emsp; |
|--|--|
| [AtlCanonicalizeUrl](../atl/reference/atl-http-utility-functions.md#atlcanonicalizeurl) | Appelez cette fonction pour rendre canonique une URL, notamment afin de convertir les caractères et espaces non sécurisés en séquences d'échappement. |
| [AtlCombineUrl](../atl/reference/atl-http-utility-functions.md#atlcombineurl) | Appelez cette fonction pour associer une URL de base et une URL relative en une URL unique et canonique. |
| [AtlEscapeUrl](../atl/reference/atl-http-utility-functions.md#atlescapeurl) | Appelez cette fonction pour convertir tous les caractères non sécurisés en séquences d'échappement. |
| [AtlGetDefaultUrlPort](../atl/reference/atl-http-utility-functions.md#atlgetdefaulturlport) | Appelez cette fonction pour obtenir le numéro de port par défaut associé à un protocole ou un schéma Internet particulier. |
| [AtlHexValue](../atl/reference/atl-text-encoding-functions.md#atlhexvalue) | Appelez cette fonction pour obtenir la valeur numérique d'un chiffre hexadécimal. |
| [AtlIsUnsafeUrlChar](../atl/reference/atl-http-utility-functions.md#atlisunsafeurlchar) | Appelez cette fonction pour déterminer si un caractère peut être utilisé de manière sécurisée dans une URL. |
| [AtlUnescapeUrl](../atl/reference/atl-http-utility-functions.md#atlunescapeurl) | Appelez cette fonction pour convertir les caractères ayant fait l'objet d'une séquence d'échappement vers leurs valeurs d'origine. |
| [SystemTimeToHttpDate](../atl/reference/atl-http-utility-functions.md#systemtimetohttpdate) | Appelez cette fonction pour convertir une heure système en une chaîne au format approprié pour être utilisée dans les en-têtes HTTP. |
| [ATLPath::AddBackslash](../atl/reference/atl-path-functions.md#addbackslash) | Cette fonction est un wrapper surchargé pour [PathAddBackslash] (/Windows/Desktop/API/shlwapi/NF-shlwapi-pathaddbackslasha |
| ). |
| [ATLPath::AddExtension](../atl/reference/atl-path-functions.md#addextension) | Cette fonction est un wrapper surchargé pour [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw). |
| [ATLPath::Append](../atl/reference/atl-path-functions.md#append) | Cette fonction est un wrapper surchargé pour [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw). |
| [ATLPath::BuildRoot](../atl/reference/atl-path-functions.md#buildroot) | Cette fonction est un wrapper surchargé pour [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw). |
| [ATLPath::Canonicalize](../atl/reference/atl-path-functions.md#canonicalize) | Cette fonction est un wrapper surchargé pour [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew). |
| [ATLPath::Combine](../atl/reference/atl-path-functions.md#combine) | Cette fonction est un wrapper surchargé pour [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew). |
| [ATLPath::CommonPrefix](../atl/reference/atl-path-functions.md#commonprefix) | Cette fonction est un wrapper surchargé pour [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw). |
| [ATLPath::CompactPath](../atl/reference/atl-path-functions.md#compactpath) | Cette fonction est un wrapper surchargé pour [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw). |
| [ATLPath::CompactPathEx](../atl/reference/atl-path-functions.md#compactpathex) | Cette fonction est un wrapper surchargé pour [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw). |
| [ATLPath::FileExists](../atl/reference/atl-path-functions.md#fileexists) | Cette fonction est un wrapper surchargé pour [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw). |
| [ATLPath::FindExtension](../atl/reference/atl-path-functions.md#findextension) | Cette fonction est un wrapper surchargé pour [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw). |
| [ATLPath::FindFileName](../atl/reference/atl-path-functions.md#findfilename) | Cette fonction est un wrapper surchargé pour [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew). |
| [ATLPath::GetDriveNumber](../atl/reference/atl-path-functions.md#getdrivenumber) | Cette fonction est un wrapper surchargé pour [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw). |
| [ATLPath::IsDirectory](../atl/reference/atl-path-functions.md#isdirectory) | Cette fonction est un wrapper surchargé pour [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw). |
| [ATLPath::IsFileSpec](../atl/reference/atl-path-functions.md#isfilespec) | Cette fonction est un wrapper surchargé pour [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw). |
| [ATLPath::IsPrefix](../atl/reference/atl-path-functions.md#isprefix) | Cette fonction est un wrapper surchargé pour [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw). |
| [ATLPath::IsRelative](../atl/reference/atl-path-functions.md#isrelative) | Cette fonction est un wrapper surchargé pour [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew). |
| [ATLPath::IsRoot](../atl/reference/atl-path-functions.md#isroot) | Cette fonction est un wrapper surchargé pour [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw). |
| [ATLPath::IsSameRoot](../atl/reference/atl-path-functions.md#issameroot) | Cette fonction est un wrapper surchargé pour [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw). |
| [ATLPath::IsUNC](../atl/reference/atl-path-functions.md#isunc) | Cette fonction est un wrapper surchargé pour [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw). |
| [ATLPath::IsUNCServer](../atl/reference/atl-path-functions.md#isuncserver) | Cette fonction est un wrapper surchargé pour [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw). |
| [ATLPath::IsUNCServerShare](../atl/reference/atl-path-functions.md#isuncservershare) | Cette fonction est un wrapper surchargé pour [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew). |
| [ATLPath::MakePretty](../atl/reference/atl-path-functions.md#makepretty) | Cette fonction est un wrapper surchargé pour [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw). |
| [ATLPath::MatchSpec](../atl/reference/atl-path-functions.md#matchspec) | Cette fonction est un wrapper surchargé pour [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw). |
| [ATLPath::QuoteSpaces](../atl/reference/atl-path-functions.md#quotespaces) | Cette fonction est un wrapper surchargé pour [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw). |
| [ATLPath::RelativePathTo](../atl/reference/atl-path-functions.md#relativepathto) | Cette fonction est un wrapper surchargé pour [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow). |
| [ATLPath::RemoveArgs](../atl/reference/atl-path-functions.md#removeargs) | Cette fonction est un wrapper surchargé pour [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw). |
| [ATLPath::RemoveBackslash](../atl/reference/atl-path-functions.md#removebackslash) | Cette fonction est un wrapper surchargé pour [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw). |
| [ATLPath::RemoveBlanks](../atl/reference/atl-path-functions.md#removeblanks) | Cette fonction est un wrapper surchargé pour [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw). |
| [ATLPath::RemoveExtension](../atl/reference/atl-path-functions.md#removeextension) | Cette fonction est un wrapper surchargé pour [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw). |
| [ATLPath::RemoveFileSpec](../atl/reference/atl-path-functions.md#removefilespec) | Cette fonction est un wrapper surchargé pour [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw). |
| [ATLPath::RenameExtension](../atl/reference/atl-path-functions.md#renameextension) | Cette fonction est un wrapper surchargé pour [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw). |
| [ATLPath::SkipRoot](../atl/reference/atl-path-functions.md#skiproot) | Cette fonction est un wrapper surchargé pour [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw). |
| [ATLPath::StripPath](../atl/reference/atl-path-functions.md#strippath) | Cette fonction est un wrapper surchargé pour [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw). |
| [ATLPath::StripToRoot](../atl/reference/atl-path-functions.md#striptoroot) | Cette fonction est un wrapper surchargé pour [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw). |
| [ATLPath::UnquoteSpaces](../atl/reference/atl-path-functions.md#unquotespaces) | Cette fonction est un wrapper surchargé pour [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw). |

## <a name="see-also"></a>Voir aussi

[Concepts](../atl/active-template-library-atl-concepts.md)<br/>
[Composants de bureau COM ATL](../atl/atl-com-desktop-components.md)
