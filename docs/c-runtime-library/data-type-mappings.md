---
title: "Mappages de types de données | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _TXCHAR
- _TUCHAR
- _TINT
- _TSCHAR
- _TCHAR
- TCHAR::H
- TCHAR
- _T
- _TEXT
dev_langs: C++
helpviewer_keywords:
- _TXCHAR type
- TINT type
- _TCHAR type
- TSCHAR type
- TEXT type
- TCHAR type
- TCHAR.H data types, mappings defined in
- generic-text data types
- _TINT type
- TUCHAR type
- TXCHAR type
- _TSCHAR type
- T type
- _TUCHAR type
- _TEXT type
- _T type
ms.assetid: 4e573c05-8800-468b-ae5f-76ff7409835e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 217290399a03174e599117077b27116a86808f7f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="data-type-mappings"></a>Mappages de types de données
Ces mappages de types de données sont définis dans TCHAR.H et varient selon que la constante `_UNICODE` ou `_MBCS` a été définie dans votre programme.  
  
 Pour plus d’informations, consultez [Utilisation de types de données TCHAR.H avec _MBCS](../text/using-tchar-h-data-types-with-mbcs-code.md).  
  
### <a name="generic-text-data-type-mappings"></a>Mappages de types de données de texte générique  
  
|Texte générique<br /><br /> nom de type de données|SBCS (_UNICODE,<br /><br /> _MBCS non<br /><br /> définis)|_MBCS<br /><br /> définir|_UNICODE<br /><br /> définir|  
|--------------------------------------|----------------------------------------------------|------------------------|---------------------------|  
|`_TCHAR`|`char`|`char`|`wchar_t`|  
|`_tfinddata_t`|`_finddata_t`|`_finddata_t`|`_wfinddata_t`|  
|`_tfinddata64_t`|`__finddata64_t`|`__finddata64_t`|`__wfinddata64_t`|  
|`_tfinddatai64_t`|`_finddatai64_t`|`_finddatai64_t`|`_wfinddatai64_t`|  
|`_TINT`|`int`|`int`|`wint_t`|  
|`_TSCHAR`|`signed char`|`signed char`|`wchar_t`|  
|`_TUCHAR`|`unsigned char`|`unsigned char`|`wchar_t`|  
|`_TXCHAR`|`char`|`unsigned char`|`wchar_t`|  
|`_T` ou `_TEXT`|Aucun effet (supprimé par le préprocesseur)|Aucun effet (supprimé par le préprocesseur)|`L` (convertit le caractère suivant ou la chaîne suivante en son équivalent Unicode)|  
  
## <a name="see-also"></a>Voir aussi  
 [Mappages de texte générique](../c-runtime-library/generic-text-mappings.md)   
 [Mappages de constantes et de variables globales](../c-runtime-library/constant-and-global-variable-mappings.md)   
 [Mappages de routine](../c-runtime-library/routine-mappings.md)   
 [Exemple de programme de texte générique](../c-runtime-library/a-sample-generic-text-program.md)   
 [Utilisation de mappages de texte générique](../c-runtime-library/using-generic-text-mappings.md)