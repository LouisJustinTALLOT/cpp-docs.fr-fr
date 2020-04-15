---
title: Documents actifs
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC]
- active documents [MFC], requirements
- view objects [MFC], requirements
- OLE [MFC], active documents
- views [MFC], active documents
- active documents [MFC], views
ms.assetid: 1378f18e-aaa6-420b-8501-4b974905baa0
ms.openlocfilehash: cbea3e032932477006820c5a71fbbf3e40123bdf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322082"
---
# <a name="active-documents"></a>Documents actifs

Les documents actifs étendent la technologie de document composé OLE. Ces extensions sont fournies sous la forme d’autres interfaces qui gèrent les vues, afin que les objets puissent s’exécuter dans des conteneurs tout en conservant le contrôle de l’affichage et des fonctions d’impression. Ce processus permet d'afficher des documents dans des frames étrangers (tels que le Classeur Microsoft Office ou Microsoft Internet Explorer) et dans des frames natifs (tels que les propres ports de vue du produit).

Cette section décrit les exigences fonctionnelles [pour les documents actifs](#requirements_for_active_documents). Le document actif possède un jeu de données et a accès au stockage dans lequel les données peuvent être enregistrées et récupérées. Il peut créer et gérer une ou plusieurs vues sur ses données. En plus de prendre en charge l'incorporation et les interfaces d'activation en place classiques des documents OLE, le document actif communique sa capacité à créer des vues via `IOleDocument`. Dans cette interface, le conteneur peut demander à créer (et énumérer) les vues que le document actif peut afficher. Dans cette interface, le document actif peut également fournir des informations diverses sur lui-même, par exemple s'il prend en charge plusieurs vues ou rectangles complexes.

Ce qui `IOleDocument` suit est l’interface. Notez `IEnumOleDocumentViews` que l’interface est un enumérateur OLE standard pour `IOleDocumentView*` les types.

```
interface IOleDocument : IUnknown
    {
    HRESULT CreateView(
        [in] IOleInPlaceSite *pIPSite,
        [in] IStream *pstm,
        [in] DWORD dwReserved,
        [out] IOleDocumentView **ppView);

    HRESULT GetDocMiscStatus([out] DWORD *pdwStatus);

    HRESULT EnumViews(
        [out] IEnumOleDocumentViews **ppEnum,
        [out] IOleDocumentView **ppView);
    }
```

Chaque document actif doit avoir un fournisseur de frame de vue avec cette interface. Si le document n'est pas incorporé dans un conteneur, le serveur de document actif lui-même doit fournir le frame de vue. Toutefois, lorsque le document actif est incorporé dans un conteneur de documents actifs, le conteneur fournit le frame de vue.

Un document actif peut créer un ou plusieurs types de [vues](#requirements_for_view_objects) de ses données (par exemple, normale, contour, mise en page, et ainsi de suite). Les vues agissent comme des filtres dans lesquels les données peuvent être affichées. Même si le document n’a qu’un seul type de vue, vous pouvez toujours prendre en charge plusieurs vues comme moyen de prendre en charge la nouvelle fonctionnalité de fenêtre (par exemple, l’élément **Nouvelle Fenêtre** sur le menu **Fenêtre** dans les applications Office).

## <a name="requirements-for-active-documents"></a><a name="requirements_for_active_documents"></a>Exigences pour les documents actifs

Un document actif qui peut être affiché dans un conteneur de documents actifs doit :

- Utiliser les fichiers composés OLE comme mécanisme de stockage en implémentant `IPersistStorage`.

- Prendre en charge les caractéristiques d’intégration de base des documents OLE, y compris **Create From File**. Cela rend nécessaire les interfaces `IPersistFile`, `IOleObject` et `IDataObject`.

- Prendre en charge une ou plusieurs vues, chacune avec la fonctionnalité d'activation en place. Autrement dit, les vues `IOleDocumentView` doivent prendre en `IOleInPlaceObject` charge `IOleInPlaceActiveObject` l’interface ainsi `IOleInPlaceSite` `IOleInPlaceFrame` que les interfaces et (en utilisant le conteneur et les interfaces).

- Prendre en charge les interfaces de document actif standard `IOleDocument`, `IOleCommandTarget` et `IPrint`.

Savoir quand et comment utiliser les interfaces côté conteneur est nécessaire pour les exigences.

## <a name="requirements-for-view-objects"></a><a name="requirements_for_view_objects"></a>Exigences pour les objets de vue

Un document actif peut créer une ou plusieurs vues de ses données. Fonctionnellement, ces vues sont comme les ports d'une méthode particulière permettant d'afficher les données. Si un document actif ne prend en charge qu'une vue, le document actif et cette vue peuvent être implémentés en utilisant une seule classe. `IOleDocument::CreateView`retourne le pointeur `IOleDocumentView` d’interface du même objet.

Pour être représenté dans un conteneur de documents `IOleInPlaceObject` `IOleInPlaceActiveObject` actif, `IOleDocumentView`un composant de vue doit prendre en charge et en plus de :

```
interface IOleDocumentView : IUnknown
    {
    HRESULT SetInPlaceSite([in] IOleInPlaceSite *pIPSite);
    HRESULT GetInPlaceSite([out] IOleInPlaceSite **ppIPSite);
    HRESULT GetDocument([out] IUnknown **ppunk);
    [input_sync] HRESULT SetRect([in] LPRECT prcView);
    HRESULT GetRect([in] LPRECT prcView);
    [input_sync] HRESULT SetRectComplex(
        [in] LPRECT prcView,
        [in] LPRECT prcHScroll,
        [in] LPRECT prcVScroll,
        [in] LPRECT prcSizeBox);
    HRESULT Show([in] BOOL fShow);
    HRESULT UIActivate([in] BOOL fUIActivate);
    HRESULT Open(void);
    HRESULT CloseView([in] DWORD dwReserved);
    HRESULT SaveViewState([in] IStream *pstm);
    HRESULT ApplyViewState([in] IStream *pstm);
    HRESULT Clone(
        [in] IOleInPlaceSite *pIPSiteNew,
        [out] IOleDocumentView **ppViewNew);
    }
```

Chaque vue a un site de vue associé, qui encapsule le frame de la vue et le port de vue (HWND et une zone rectangulaire dans cette fenêtre). Le site expose cette fonctionnalité `IOleInPlaceSite` par l’interface standard. Notez qu'il est possible d'avoir plusieurs port d'affichage sur un seul HWND.

En général, chaque type de vue a une représentation affichée différente. Par conséquent les vues et les sites de correspondance de vue doivent implémenter les interfaces d'impression si `IPrint` et `IContinueCallback`, respectivement. Le cadre de vue doit `IPrint` négocier avec le fournisseur de vue à travers quand l’impression commence, de sorte que les en-têtes, les pieds, les marges, et les éléments connexes sont imprimés correctement. Le fournisseur d'affichage notifie le frame des événements liés à l'impression via `IContinueCallback`. Pour plus d’informations sur l’utilisation de ces interfaces, voir [l’impression programmatique](../mfc/programmatic-printing.md).

Notez que si un document actif ne prend en charge qu'une vue, le document actif et cette vue peuvent être implémentés en utilisant une seule classe concrète. `IOleDocument::CreateView`renvoie simplement le `IOleDocumentView` pointeur d’interface du même objet. En bref, il n'est pas nécessaire d'avoir deux instances d'objet distinctes lorsqu'une seule vue est requise.

Un objet de vue peut également être une cible de commande. `IOleCommandTarget` En implémentant une vue peut recevoir des commandes qui proviennent de l’interface utilisateur du conteneur (tels que **New**, **Open**, **Save As**, **Imprimer** sur le menu **Fichier;** et **Copier**, **Coller**, **Annuler** sur le menu **Edit).** Pour plus d’informations, voir [Les cibles de traitement et de commandement des messages](../mfc/message-handling-and-command-targets.md).

## <a name="see-also"></a>Voir aussi

[Documents actifs (contenance)](../mfc/active-document-containment.md)
