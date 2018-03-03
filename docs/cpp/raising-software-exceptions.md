---
title: "Le déclenchement d’Exceptions logicielles | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- run-time errors, treating as exceptions
- exception handling [C++], errors as exceptions
- exceptions [C++], flagging errors as exceptions
- errors [C++], treating as exceptions
- exception handling [C++], detecting errors
- structured exception handling [C++], errors as exceptions
- exceptions [C++], software
- RaiseException function
- software exceptions [C++]
- formats [C++], exception codes
ms.assetid: be1376c3-c46a-4f52-ad1d-c2362840746a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4eb616945a831502077066bdf306bef306f543eb
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="raising-software-exceptions"></a>Déclenchement d'exceptions logicielles
Certaines des sources les plus courantes d'erreurs de programme ne sont pas marquées en tant qu'exceptions par le système. Par exemple, si vous essayez d'allouer un bloc de mémoire mais que la mémoire disponible est insuffisante, la fonction runtime ou API ne déclenche pas d'exception mais retourne un code d'erreur.  
  
 Toutefois, vous pouvez traiter n’importe quelle condition comme une exception en détectant cette condition dans votre code, puis le rapports en appelant le [RaiseException](http://msdn.microsoft.com/library/windows/desktop/ms680552) (fonction). Le fait de marquer les erreurs de cette manière vous permet de tirer parti de la gestion structurée des exceptions pour tout type d'erreur d'exécution.  
  
 Pour utiliser la gestion structurée des exceptions avec des erreurs :  
  
-   Définissez votre propre code d'exception pour l'événement.  
  
-   Appelez **RaiseException** lorsque vous détectez un problème.  
  
-   Utilisez les filtres de gestion des exceptions pour tester le code d'exception que vous avez défini.  
  
 Le \<winerror.h > fichier présente le format des codes d’exception. Pour veiller à ne pas définir un code qui est en conflit avec un code d'exception existant, définissez le troisième bit le plus significatif à 1. Les quatre bits les plus significatifs doivent être définis comme indiqué dans le tableau suivant.  
  
|Bits|Paramètre binaire recommandé|Description|  
|----------|--------------------------------|-----------------|  
|31-30|11|Ces deux bits décrivent l'état de base du code : 11 = erreur, 00 = succès, 01 = informatif, 10 = avertissement.|  
|29|1|Bit client. Affectez-lui la valeur 1 pour les codes définis par l'utilisateur.|  
|28|0|Bit réservé. (Laissez la valeur 0.)|  
  
 Vous pouvez définir les deux premiers bits à un paramètre autre 11 binaire, bien que le paramètre « erreur » soit appropriée pour la plupart des exceptions. Veillez à définir les bits 29 et 28 comme indiqué dans le tableau précédent.  
  
 Le code d’erreur résultant doit donc contenir les quatre bits le plus élevés la valeur e hexadécimale. Par exemple, les définitions suivantes définissent les codes d’exception pas de conflit entre les codes d’exception de Windows. (Toutefois, vous pouvez être amené à vérifier quels codes sont utilisés par les DLL tierces.)  
  
```  
#define STATUS_INSUFFICIENT_MEM       0xE0000001  
#define STATUS_FILE_BAD_FORMAT        0xE0000002  
```  
  
 Après avoir défini un code d'exception, vous pouvez l'utiliser pour lever une exception. Par exemple, le code suivant déclenche l'exception STATUS_INSUFFICIENT_MEM en réponse à un problème d'allocation de mémoire :  
  
```  
lpstr = _malloc( nBufferSize );  
if (lpstr == NULL)  
    RaiseException( STATUS_INSUFFICIENT_MEM, 0, 0, 0);  
```  
  
 Si vous souhaitez déclencher simplement une exception, vous pouvez définir les trois derniers paramètres à 0. Les trois derniers paramètres sont utiles pour transmettre des informations supplémentaires et définir un indicateur qui empêche les gestionnaires de poursuivre l'exécution. Consultez le [RaiseException](http://msdn.microsoft.com/library/windows/desktop/ms680552) de fonction dans le [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)] pour plus d’informations.  
  
 Dans vos filtres de gestion des exceptions, vous pouvez ensuite tester les codes que vous avez définis. Exemple :  
  
```  
__try {  
    ...  
}  
__except (GetExceptionCode() == STATUS_INSUFFICIENT_MEM ||  
        GetExceptionCode() == STATUS_FILE_BAD_FORMAT )  
```  
  
## <a name="see-also"></a>Voir aussi  
 [L’écriture d’un gestionnaire d’exceptions](../cpp/writing-an-exception-handler.md)   
 [Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)