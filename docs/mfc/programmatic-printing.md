---
description: 'En savoir plus sur : l’impression par programmation'
title: Impression par programmation
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], active documents
- active documents [MFC], printing
- printing [MFC], programmatic
- IPrint interface
- printing [MFC]
ms.assetid: 3db0945b-5e13-4be4-86a0-6aecdae565bd
ms.openlocfilehash: c97a3938a97970e1479add4f62b68250845ba7e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154693"
---
# <a name="programmatic-printing"></a>Impression par programmation

OLE a fourni les moyens d’identifier de façon unique les documents persistants ( `GetClassFile` ) et de les charger dans leur code associé ( `CoCreateInstance` , `QueryInterface(IID_IPersistFile)` ,, `QueryInterface(IID_IPersistStorage)` `IPersistFile::Load` et `IPersistStorage::Load` ). Pour activer davantage l'impression de documents, la relation contenant-contenu de document actif (en utilisant une conception OLE existante non fournie avec OLE 2.0 à l'origine) présente une interface standard de base d'impression, `IPrint`, généralement disponible via un objet qui peut charger l'état permanent du type de document. Chaque vue d’un document actif peut éventuellement prendre en charge l' `IPrint` interface pour fournir ces fonctionnalités.

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

Les clients et les conteneurs utilisent simplement `IPrint::Print` pour demander au document de s’imprimer une fois ce document chargé, en spécifiant des indicateurs de contrôle d’impression, l’appareil cible, les pages à imprimer et des options supplémentaires. Le client peut également contrôler la suite de l'impression via l'interface `IContinueCallback` (voir ci-dessous).

En outre, `IPrint::SetInitialPageNum` prend en charge la possibilité d’imprimer une série de documents comme un tout en numérotant les pages en toute transparence, ce qui est évidemment un avantage pour les conteneurs de documents actifs tels que le classeur Office. `IPrint::GetPageInfo` facilite l’affichage des informations de pagination en permettant à l’appelant de récupérer le numéro de page de début précédemment passé à `SetInitialPageNum` (ou le numéro de page de démarrage par défaut interne du document) et le nombre de pages dans le document.

Les objets prenant en charge `IPrint` sont marqués dans le Registre avec la clé "Printable" stockée sous le CLSID de l'objet :

HKEY_CLASSES_ROOT\CLSID\\ {...} \Printable

`IPrint` est généralement implémentée sur le même objet qui prend en charge `IPersistFile` ou `IPersistStorage`. Les appelants notent la possibilité d'imprimer de façon programmée l'état permanent d'une certaine classe en recherchant la clé "Printable" dans le Registre. Actuellement, « imprimable » indique la prise en charge d’au moins `IPrint` ; d’autres interfaces peuvent être définies à l’avenir et disponibles par l’intermédiaire `QueryInterface` de, où `IPrint` représente simplement le niveau de base de la prise en charge.

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

Cette interface est conçue pour être utile en tant que fonction de rappel de continuation générique qui remplace les différentes procédures de continuation dans l’API Win32 (comme `AbortProc` pour l’impression et l' `EnumMetafileProc` énumération de métafichiers). Cette conception d'interface est utile dans une grande variété de processus longs.

Dans les cas les plus génériques, la `IContinueCallback::FContinue` fonction est appelée régulièrement par n’importe quel processus long. L’objet récepteur retourne S_OK pour poursuivre l’opération et S_FALSE d’arrêter la procédure dès que possible.

`FContinue`Toutefois, n’est pas utilisé dans le contexte de `IPrint::Print` ; au lieu de cela, l’impression utilise `IContinueCallback::FContinuePrint` . Tout objet d’impression doit appeler périodiquement `FContinuePrinting` le nombre de pages qui ont été imprimées, le numéro de la page en cours d’impression et une chaîne supplémentaire qui décrit l’état d’impression que le client peut choisir d’afficher à l’utilisateur (par exemple, « page 5 sur 19 »).

## <a name="see-also"></a>Voir aussi

[Conteneurs de documents actifs](../mfc/active-document-containers.md)
