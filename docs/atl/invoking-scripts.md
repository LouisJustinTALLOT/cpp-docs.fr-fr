---
title: Appel de Scripts (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- StringRegister method
- scripts, invoking registry in ATL
ms.assetid: eabd41ee-586b-4266-9e92-5aaad04b73a4
ms.openlocfilehash: 6ca744ced53677550e7b77f44d4f6550da744372
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62250465"
---
# <a name="invoking-scripts"></a>Appel de Scripts

[À l’aide des paramètres remplaçables (le préprocesseur de Registrar)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) décrit les mappages de remplacement et mentionne la méthode Registrar **AddReplacement**. Le bureau d’enregistrement a huit méthodes spécifiques des scripts, et toutes sont décrites dans le tableau suivant.

|Méthode|Description de la syntaxe|
|------------|-------------------------|
|**ResourceRegister**|**HRESULT ResourceRegister( LPCOLESTR**  *resFileName* **, UINT**  `nID` **, LPCOLESTR**  `szType` **);**<br /><br /> Inscrit le script contenu dans la ressource d’un module. *resFileName* indique le chemin d’accès UNC au module lui-même. *nID* et *szType* contiennent respectivement les ID et le type de la ressource.|
|**ResourceUnregister**|**HRESULT ResourceUnregister( LPCOLESTR**  *resFileName* **, UINT**  `nID` **, LPCOLESTR**  `szType` **);**<br /><br /> Désinscrit le script contenu dans la ressource d’un module. *resFileName* indique le chemin d’accès UNC au module lui-même. *nID* et *szType* contiennent respectivement les ID et le type de la ressource.|
|**ResourceRegisterSz**|**HRESULT ResourceRegisterSz( LPCOLESTR**  *resFileName* **, LPCOLESTR**  *szID* **, LPCOLESTR**  `szType` **);**<br /><br /> Inscrit le script contenu dans la ressource d’un module. *resFileName* indique le chemin d’accès UNC au module lui-même. *szID* et *szType* contiennent respectivement identificateur de chaîne et le type, de la ressource.|
|**ResourceUnregisterSz**|**HRESULT ResourceUnregisterSz( LPCOLESTR**  *resFileName* **, LPCOLESTR**  *szID* **, LPCOLESTR**  `szType` **);**<br /><br /> Désinscrit le script contenu dans la ressource d’un module. *resFileName* indique le chemin d’accès UNC au module lui-même. *szID* et *szType* contiennent respectivement identificateur de chaîne et le type, de la ressource.|
|**FileRegister**|**HRESULT FileRegister (LPCOLESTR***fileName***) ;**<br /><br /> Inscrit le script dans un fichier. *nom de fichier* est un chemin UNC vers un fichier qui contienne un script de ressources (ou qui est).|
|**FileUnregister**|**HRESULT FileUnregister( LPCOLESTR**  *fileName*  **);**<br /><br /> Annule l’inscription du script dans un fichier. *nom de fichier* est un chemin UNC vers un fichier qui contienne un script de ressources (ou qui est).|
|**StringRegister**|**HRESULT StringRegister (LPCOLESTR***données***) ;**<br /><br /> Inscrit le script dans une chaîne. *données* contient le script lui-même.|
|**StringUnregister**|**HRESULT StringUnregister( LPCOLESTR**  *data*  **);**<br /><br /> Annule l’inscription du script dans une chaîne. *données* contient le script lui-même.|

**ResourceRegisterSz** et **ResourceUnregisterSz**, sont similaires aux **ResourceRegister** et **ResourceUnregister**, mais vous permettent de spécifier une chaîne identificateur.

Les méthodes **FileRegister** et **FileUnregister** sont utiles si vous ne souhaitez pas que le script dans une ressource ou si vous souhaitez que le script dans son propre fichier. Les méthodes **StringRegister** et **StringUnregister** permettre au fichier .rgs à stocker dans une chaîne allouée dynamiquement.

## <a name="see-also"></a>Voir aussi

[Création de scripts d’inscription](../atl/creating-registrar-scripts.md)
