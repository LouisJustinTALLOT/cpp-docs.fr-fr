---
description: 'En savoir plus sur : documents actifs'
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
ms.openlocfilehash: cae0eda775670867d5e36b4f2b9ec895a5dc3eb7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150304"
---
# <a name="active-documents"></a>Documents actifs

Les documents actifs étendent la technologie de document composé OLE. Ces extensions sont fournies sous la forme d’autres interfaces qui gèrent les vues, afin que les objets puissent s’exécuter dans des conteneurs tout en conservant le contrôle de l’affichage et des fonctions d’impression. Ce processus permet d'afficher des documents dans des frames étrangers (tels que le Classeur Microsoft Office ou Microsoft Internet Explorer) et dans des frames natifs (tels que les propres ports de vue du produit).

Cette section décrit les spécifications fonctionnelles [pour les documents actifs](#requirements_for_active_documents). Le document actif possède un jeu de données et a accès au stockage dans lequel les données peuvent être enregistrées et récupérées. Il peut créer et gérer une ou plusieurs vues sur ses données. En plus de prendre en charge l'incorporation et les interfaces d'activation en place classiques des documents OLE, le document actif communique sa capacité à créer des vues via `IOleDocument`. Dans cette interface, le conteneur peut demander à créer (et énumérer) les vues que le document actif peut afficher. Dans cette interface, le document actif peut également fournir des informations diverses sur lui-même, par exemple s'il prend en charge plusieurs vues ou rectangles complexes.

L’interface est la suivante `IOleDocument` . Notez que l' `IEnumOleDocumentViews` interface est un ÉNUMÉRATEUR OLE standard pour les `IOleDocumentView*` types.

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

Un document actif peut créer un ou plusieurs types de [vues](#requirements_for_view_objects) de ses données (par exemple, normal, plan, mise en page, etc.). Les vues agissent comme des filtres dans lesquels les données peuvent être affichées. Même si le document n’a qu’un seul type de vue, vous souhaiterez peut-être toujours prendre en charge plusieurs vues comme un moyen de prendre en charge les nouvelles fonctionnalités de fenêtre (par exemple, le nouvel élément de **fenêtre** dans le menu **fenêtre** des applications Office).

## <a name="requirements-for-active-documents"></a><a name="requirements_for_active_documents"></a> Conditions requises pour les documents actifs

Un document actif qui peut être affiché dans un conteneur de documents actifs doit :

- Utiliser les fichiers composés OLE comme mécanisme de stockage en implémentant `IPersistStorage`.

- Prendre en charge les fonctionnalités d’incorporation de base des documents OLE, y compris **créer à partir d’un fichier**. Cela rend nécessaire les interfaces `IPersistFile`, `IOleObject` et `IDataObject`.

- Prendre en charge une ou plusieurs vues, chacune avec la fonctionnalité d'activation en place. Autrement dit, les vues doivent prendre en charge l’interface, ainsi `IOleDocumentView` que les interfaces `IOleInPlaceObject` et `IOleInPlaceActiveObject` (à l’aide des `IOleInPlaceSite` interfaces et du conteneur `IOleInPlaceFrame` ).

- Prendre en charge les interfaces de document actif standard `IOleDocument`, `IOleCommandTarget` et `IPrint`.

Savoir quand et comment utiliser les interfaces côté conteneur est nécessaire pour les exigences.

## <a name="requirements-for-view-objects"></a><a name="requirements_for_view_objects"></a> Conditions requises pour les objets de vue

Un document actif peut créer une ou plusieurs vues de ses données. Fonctionnellement, ces vues sont comme les ports d'une méthode particulière permettant d'afficher les données. Si un document actif ne prend en charge qu'une vue, le document actif et cette vue peuvent être implémentés en utilisant une seule classe. `IOleDocument::CreateView` retourne le pointeur d’interface de cet objet `IOleDocumentView` .

Pour être représenté dans un conteneur de documents actifs, un composant de vue doit prendre en charge `IOleInPlaceObject` et `IOleInPlaceActiveObject` en plus des `IOleDocumentView` éléments suivants :

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

Chaque vue a un site de vue associé, qui encapsule le frame de la vue et le port de vue (HWND et une zone rectangulaire dans cette fenêtre). Le site expose cette fonctionnalité par le biais de l' `IOleInPlaceSite` interface standard. Notez qu'il est possible d'avoir plusieurs port d'affichage sur un seul HWND.

En général, chaque type de vue a une représentation affichée différente. Par conséquent les vues et les sites de correspondance de vue doivent implémenter les interfaces d'impression si `IPrint` et `IContinueCallback`, respectivement. Le frame de vue doit négocier avec le fournisseur d’affichage par le biais de `IPrint` lorsque l’impression commence, afin que les en-têtes, les pieds de page, les marges et les éléments associés soient correctement imprimés. Le fournisseur d'affichage notifie le frame des événements liés à l'impression via `IContinueCallback`. Pour plus d’informations sur l’utilisation de ces interfaces, consultez [impression par programmation](programmatic-printing.md).

Notez que si un document actif ne prend en charge qu'une vue, le document actif et cette vue peuvent être implémentés en utilisant une seule classe concrète. `IOleDocument::CreateView` retourne simplement le pointeur d’interface de cet objet `IOleDocumentView` . En bref, il n'est pas nécessaire d'avoir deux instances d'objet distinctes lorsqu'une seule vue est requise.

Un objet de vue peut également être une cible de commande. En implémentant `IOleCommandTarget` une vue, vous pouvez recevoir des commandes qui proviennent de l’interface utilisateur du conteneur (par exemple, **nouveau**, **ouvrir**, **Enregistrer sous**, **Imprimer** dans le menu **fichier** et **copier**, **coller**, **Annuler** dans le menu **Edition** ). Pour plus d’informations, consultez [gestion des messages et cibles des commandes](message-handling-and-command-targets.md).

## <a name="see-also"></a>Voir aussi

[Relation contenant-contenu de document actif](active-document-containment.md)
