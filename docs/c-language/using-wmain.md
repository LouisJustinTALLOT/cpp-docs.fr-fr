---
title: Utilisation de wmain | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- wmain function
ms.assetid: d0300812-adc4-40c6-bba3-b2da25468c80
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 3dcad032c8a77309d66f02a1b58c46a4e6d526b8
ms.contentlocale: fr-fr
ms.lasthandoff: 10/09/2017

---
# <a name="using-wmain"></a>Utilisation de wmain
**Section spécifique à Microsoft**  
  
 Dans le modèle de programmation Unicode, vous pouvez définir une version à caractères larges de la fonction **main**. Utilisez **wmain** au lieu de **main** si vous souhaitez écrire du code portable conforme au modèle de programmation Unicode.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )  
```  
  
## <a name="remarks"></a>Remarques  
 Vous déclarez des paramètres formels à **wmain** à l'aide d'un format identique à **main**. Vous pouvez ensuite passer des arguments à caractère élargi et éventuellement un pointeur d’environnement à caractère élargi au programme. Les paramètres `argv` et `envp` de la fonction **wmain** sont de type `wchar_t*`. Exemple :  
  
 Si votre programme utilise une fonction **main**, l'environnement de caractère multioctets est créé par la bibliothèque Runtime au démarrage du programme. Une copie de l'environnement à caractère élargi est créée uniquement lorsqu'elle est nécessaire (par exemple, par un appel des fonctions `_wgetenv` ou `_wputenv`). Au premier appel à `_wputenv`, ou à `_wgetenv` si un environnement MBCS existe déjà, un environnement de chaîne à caractères larges correspondant est créé, puis désigné par la variable globale `_wenviron`, qui est une version à caractères larges de la variable globale `_environ`. À ce moment-là, deux copies de l'environnement (MBCS et Unicode) existent simultanément et sont conservées par le système d'exploitation pendant toute la vie du programme.  
  
 De même, si votre programme utilise une fonction **wmain**, un environnement à caractère élargi est créé au moment du démarrage et une variable globale `_wenviron` pointe vers cet environnement. Un environnement MBCS (ASCII) est créé lors du premier appel de `_putenv` ou `getenv`, et la variable globale `_environ` pointe vers cet environnement.  
  
 Pour plus d'informations sur l'environnement MBCS, consultez [Internationalisation](../c-runtime-library/internationalization.md) dans le document *Référence de la bibliothèque Runtime.*  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction main et exécution du programme](../c-language/main-function-and-program-execution.md)
