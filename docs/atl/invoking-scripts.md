---
description: 'En savoir plus sur : appel de scripts'
title: Appel de scripts (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- StringRegister method
- scripts, invoking registry in ATL
ms.assetid: eabd41ee-586b-4266-9e92-5aaad04b73a4
ms.openlocfilehash: 48fc49118d93893b5cd60462fbaecfdb73d747c3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152657"
---
# <a name="invoking-scripts"></a>Appel de scripts

L' [utilisation de paramètres remplaçables (le préprocesseur du greffier)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) discute des mappages de remplacement et mentionne la méthode d’inscription **AddReplacement**. Le Bureau d’enregistrement a huit autres méthodes spécifiques aux scripts, et toutes sont décrites dans le tableau suivant.

|Méthode|Syntaxe/Description|
|------------|-------------------------|
|**ResourceRegister**|**HRESULT ResourceRegister (LPCOLESTR***resFileName* **, uint** `nID` **, LPCOLESTR** `szType` **);**      <br /><br /> Inscrit le script contenu dans la ressource d’un module. *resFileName* indique le chemin d’accès UNC au module lui-même. *nid* et *szType* contiennent respectivement l’ID et le type de la ressource.|
|**ResourceUnregister**|**HRESULT ResourceUnregister (LPCOLESTR***resFileName* **, uint** `nID` **, LPCOLESTR** `szType` **);**      <br /><br /> Annule l’inscription du script contenu dans la ressource d’un module. *resFileName* indique le chemin d’accès UNC au module lui-même. *nid* et *szType* contiennent respectivement l’ID et le type de la ressource.|
|**ResourceRegisterSz**|**HRESULT ResourceRegisterSz (LPCOLESTR***resFileName* **, LPCOLESTR***szID* **, LPCOLESTR** `szType` **);**      <br /><br /> Inscrit le script contenu dans la ressource d’un module. *resFileName* indique le chemin d’accès UNC au module lui-même. *szID* et *szType* contiennent respectivement l’identificateur de chaîne et le type de la ressource.|
|**ResourceUnregisterSz**|**HRESULT ResourceUnregisterSz (LPCOLESTR***resFileName* **, LPCOLESTR***szID* **, LPCOLESTR** `szType` **);**      <br /><br /> Annule l’inscription du script contenu dans la ressource d’un module. *resFileName* indique le chemin d’accès UNC au module lui-même. *szID* et *szType* contiennent respectivement l’identificateur de chaîne et le type de la ressource.|
|**FileRegister**|**HRESULT FileRegister (nom de***fichier* LPCOLESTR **);**    <br /><br /> Inscrit le script dans un fichier. *filename* est un chemin d’accès UNC à un fichier qui contient (ou est) un script de ressource.|
|**FileUnregister**|**HRESULT FileUnregister (nom de***fichier* LPCOLESTR **);**    <br /><br /> Annule l’inscription du script dans un fichier. *filename* est un chemin d’accès UNC à un fichier qui contient (ou est) un script de ressource.|
|**StringRegister**|**HRESULT StringRegister (***données* LPCOLESTR **);**    <br /><br /> Inscrit le script dans une chaîne. les *données* contiennent le script lui-même.|
|**StringUnregister**|**HRESULT StringUnregister (***données* LPCOLESTR **);**    <br /><br /> Annule l’inscription du script dans une chaîne. les *données* contiennent le script lui-même.|

**ResourceRegisterSz** et **ResourceUnregisterSz**, sont similaires à **ResourceRegister** et **ResourceUnregister**, mais vous permettent de spécifier un identificateur de chaîne.

Les méthodes **FileRegister** et **FileUnregister** sont utiles si vous ne souhaitez pas que le script se trouve dans une ressource ou si vous souhaitez que le script soit dans son propre fichier. Les méthodes **StringRegister** et **StringUnregister** permettent au fichier. RGS d’être stocké dans une chaîne allouée dynamiquement.

## <a name="see-also"></a>Voir aussi

[Création de scripts d’inscription](../atl/creating-registrar-scripts.md)
