---
title: Impression par programmation | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- printing [MFC], active documents
- active documents [MFC], printing
- printing [MFC], programmatic
- IPrint interface
- printing [MFC]
ms.assetid: 3db0945b-5e13-4be4-86a0-6aecdae565bd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dbbc9792fcaec6713e13b4665568017bc5ce1bdc
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930925"
---
# <a name="programmatic-printing"></a>Impression par programmation
OLE a fourni les moyens permettant d’identifier de manière unique les documents persistants (`GetClassFile`) et les charger dans leur code associé (`CoCreateInstance`, `QueryInterface(IID_IPersistFile)`, `QueryInterface(IID_IPersistStorage)`, `IPersistFile::Load`, et `IPersistStorage::Load`). Pour activer davantage l'impression de documents, la relation contenant-contenu de document actif (en utilisant une conception OLE existante non fournie avec OLE 2.0 à l'origine) présente une interface standard de base d'impression, `IPrint`, généralement disponible via un objet qui peut charger l'état permanent du type de document. Chaque vue d’un document actif peut éventuellement prend en charge les le `IPrint` interface afin de fournir ces fonctionnalités.  
  
 L'interface `IPrint` se définit de la manière suivante :  
  
```  
interface IPrint : IUnknown  
    {  
    HRESULT SetInitialPageNum([in] LONG nFirstPage);  
    HRESULT GetPageInfo(  
        [out] LONG *pnFirstPage,  
        [out] LONG *pcPages);  
    HRESULT Print(  
        [in] DWORD grfFlags,  
        [in,out] DVTARGETDEVICE **pptd,  
        [in,out] PAGESET ** ppPageSet,  
        [in,out] STGMEDIUM **ppstgmOptions,  
        [in] IContinueCallback* pCallback,  
        [in] LONG nFirstPage,  
        [out] LONG *pcPagesPrinted,  
        [out] LONG *pnPageLast);  
    };  
```  
  
 Les clients et les conteneurs utilisent simplement `IPrint::Print` pour indiquer au document s’imprime une fois qu’un document est chargé, en spécifiant les indicateurs de contrôle d’impression, le périphérique cible, les pages à imprimer et des options supplémentaires. Le client peut également contrôler la suite de l'impression via l'interface `IContinueCallback` (voir ci-dessous).  
  
 En outre, `IPrint::SetInitialPageNum` prend en charge la possibilité d’imprimer une série de documents, comme un à la numérotation des pages de façon transparente, évidemment un avantage pour les conteneurs de documents actifs tels que le classeur Office. `IPrint::GetPageInfo` rend l’affichage des informations de pagination simples en permettant à l’appelant de récupérer le démarrage de la page nombre précédemment passé à `SetInitialPageNum` (ou numéro de page de démarrage de la valeur par défaut du document interne) et le nombre de pages dans le document.  
  
 Les objets prenant en charge `IPrint` sont marqués dans le Registre avec la clé "Printable" stockée sous le CLSID de l'objet :  
  
 HKEY_CLASSES_ROOT\CLSID\\{...} \Printable  
  
 `IPrint` est généralement implémentée sur le même objet qui prend en charge `IPersistFile` ou `IPersistStorage`. Les appelants notent la possibilité d'imprimer de façon programmée l'état permanent d'une certaine classe en recherchant la clé "Printable" dans le Registre. Actuellement, « Imprimables » indique la prise en charge au moins `IPrint`; autres interfaces peuvent être définies à l’avenir qui seront ensuite accessibles via `QueryInterface` où `IPrint` simplement représente le niveau de base de prise en charge.  
  
 Pendant la procédure d'impression, vous pouvez souhaiter que le client ou le conteneur à l'origine de l'impression puisse contrôler si l'impression doit continuer. Par exemple, le conteneur peut prendre en charge une commande "Arrêter" qui doit arrêter le travail d'impression dès que possible. Pour prendre en charge cette fonctionnalité, le client d'un objet imprimable peut implémenter un petit objet récepteur de notification avec l'interface `IContinueCallback` :  
  
```  
interface IContinueCallback : IUnknown  
    {  
    HRESULT FContinue(void);  
    HRESULT FContinuePrinting(  
        [in] LONG cPagesPrinted,  
        [in] LONG nCurrentPage,  
        [in] LPOLESTR pszPrintStatus);  
    };  
```  
  
 Cette interface est conçue pour être utile en tant qu’une fonction de rappel de continuation générique qui remplace les différentes procédures de continuation dans l’API Win32 (telles que la `AbortProc` pour l’impression et `EnumMetafileProc` pour l’énumération de métafichier). Cette conception d'interface est utile dans une grande variété de processus longs.  
  
 Dans les cas plus génériques, le `IContinueCallback::FContinue` est appelée régulièrement par un processus long. L’objet récepteur retourne S_OK pour continuer l’opération et S_FALSE pour arrêter la procédure dès que possible.  
  
 `FContinue`, toutefois, n’est pas utilisé dans le contexte de `IPrint::Print`; au lieu de cela, l’impression utilise `IContinueCallback::FContinuePrint`. Tout objet d’impression doit appeler périodiquement `FContinuePrinting` en passant le nombre de pages qui ont été imprimées, le numéro de la page en cours d’impression et une chaîne supplémentaire qui décrit l’état d’impression que le client peut choisir d’afficher à l’utilisateur (par exemple, « Page 5 sur 19").  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneurs de documents actifs](../mfc/active-document-containers.md)

