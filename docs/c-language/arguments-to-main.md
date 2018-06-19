---
title: Arguments pour main | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 39824fef-05ad-461d-ae82-49447dda8060
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 544b5eaba49fff0a5f2b3111c2a5f7fe42c9b2ee
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32382492"
---
# <a name="arguments-to-main"></a>Arguments pour main
**ANSI 2.1.2.2.1** Sémantique des arguments de main  
  
 Dans Microsoft C, la fonction appelée au démarrage du programme est appelée **main**. Il n’existe aucun prototype déclaré pour **main** et cette fonction peut être définie avec zéro, deux ou trois paramètres :  
  
```  
int main( void )  
int main( int argc, char *argv[] )  
int main( int argc, char *argv[], char *envp[] )  
```  
  
 La troisième ligne ci-dessus, où **main** accepte trois paramètres, est une extension Microsoft de la norme C ANSI. Le troisième paramètre, **envp**, est un tableau de pointeurs vers des variables d’environnement. Le tableau **envp** est arrêté par un pointeur null. Pour plus d’informations sur **main** et **envp**, consultez [La fonction main et l’exécution du programme](../c-language/main-function-and-program-execution.md).  
  
 La variable **argc** ne contient jamais de valeur négative.  
  
 Le tableau de chaînes se termine par **argv[argc]**, qui contient un pointeur null.  
  
 Tous les éléments du tableau **argv** sont des pointeurs vers des chaînes.  
  
 Un programme appelé sans argument de ligne de commande reçoit une valeur de un pour **argc** lorsque le nom du fichier exécutable est placé dans **argv[0]**. Dans les versions MS-DOS antérieures à 3.0, le nom du fichier exécutable n'est pas disponible. La lettre C est placée dans **argv[0]**. Les chaînes pointées par **argv[1]** à **argv[argc - 1]** représentent des paramètres de programme.  
  
 Les paramètres **argc** et **argv** sont modifiables et conservent leurs dernières valeurs stockées entre le démarrage du programme et l’arrêt du programme.  
  
## <a name="see-also"></a>Voir aussi  
 [Environnement](../c-language/environment.md)