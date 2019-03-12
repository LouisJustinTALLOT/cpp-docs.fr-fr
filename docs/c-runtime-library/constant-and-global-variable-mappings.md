---
title: Mappage de constantes et de variables globales
ms.date: 11/04/2016
f1_keywords:
- _tenviron
- _TEOF
- _tfinddata_t
helpviewer_keywords:
- tfinddatat function
- tenviron function
- TEOF type
- _TEOF type
- generic-text mappings
- _tenviron function
- _tfinddata_t function
ms.assetid: 3af4fd3e-9ed5-4ed9-96fd-7031e5126fd1
ms.openlocfilehash: 1bd96c7a305f588a24b0c6d31b2a0132d6546574
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750193"
---
# <a name="constant-and-global-variable-mappings"></a>Mappage de constantes et de variables globales

Ces mappages de constantes de texte générique, de variables globales et de type standard sont définis dans TCHAR.H et varient selon que la constante `_UNICODE` ou `_MBCS` a été définie dans votre programme.

### <a name="generic-text-constant-and-global-variable-mappings"></a>Mappages de constantes de texte générique et de variables globales

|Texte générique - nom de l’objet|SBCS (_UNICODE, _MBCS non définis)|_MBCS défini|_UNICODE défini|
|----------------------------------|--------------------------------------------|--------------------|-----------------------|
|`_TEOF`|`EOF`|`EOF`|`WEOF`|
|`_tenviron`|`_environ`|`_environ`|`_wenviron`|
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|

## <a name="see-also"></a>Voir aussi

[Mappages de texte générique](../c-runtime-library/generic-text-mappings.md)<br/>
[Mappages de types de données](../c-runtime-library/data-type-mappings.md)<br/>
[Mappages de routine](../c-runtime-library/routine-mappings.md)<br/>
[Exemple de programme de texte générique](../c-runtime-library/a-sample-generic-text-program.md)<br/>
[Utilisation de mappages de texte générique](../c-runtime-library/using-generic-text-mappings.md)
