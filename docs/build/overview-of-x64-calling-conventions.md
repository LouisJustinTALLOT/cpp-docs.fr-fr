---
title: Vue d’ensemble de x64 Conventions d’appel | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a05db5eb-0844-4d9d-8b92-b1b2434be0ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb4071cd3223ad2ab073f84418e641b515c05112
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="overview-of-x64-calling-conventions"></a>Vue d’ensemble des conventions d’appel x64
Deux différences importantes entre x86 et [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] sont la fonction d’adressage 64 bits et un jeu de 16 bits 64 registres pour une utilisation générale. Étant donné les registres étendu ensemble, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] utilise le [__fastcall](../cpp/fastcall.md) convention d’appel et un modèle de gestion des exceptions basé sur RISC. Le `__fastcall` convention utilise des registres pour les quatre premiers arguments et le frame de pile pour passer des arguments supplémentaires.  
  
 L’option du compilateur suivante vous aide à optimiser votre application pour [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]:  
  
-   [/favor (Optimisation pour les particularités d’architecture)](../build/reference/favor-optimize-for-architecture-specifics.md)  
  
## <a name="calling-convention"></a>Convention d’appel  
 Le [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] une quatre Registre fast-convention d’appel par défaut utilise l’Interface binaire d’Application (ABI). Espace est alloué sur la pile des appels, comme un magasin de clichés instantanés pour appelés enregistrer ces registres. Il existe une correspondance univoque stricte entre les arguments pour un appel de fonction et les registres utilisés pour ces arguments. Tout argument qui ne tient pas dans 8 octets, ou n’est pas 1, 2, 4 ou 8 octets, doit être passé par référence. Il n’existe aucune tentative pour répartir un argument unique sur plusieurs registres. Le x87 pile du Registre n’est pas utilisée. Il peut être utilisé par l’appelé, mais doit être considérée comme volatile entre les appels de fonction. Virgule flottante toutes les opérations sont effectuées à l’aide du 16 registres de XMM. Arguments entiers sont passés dans les registres RCX, RDX, R8 et R9. Arguments sont passés dans XMM0L, XMM1L, XMM2L et XMM3L de virgule flottante. arguments de 16 octets sont passés par référence. Passage de paramètres est décrite en détail dans [passage de paramètres](../build/parameter-passing.md). Outre ces registres, RAX, R10, R11, XMM4 et XMM5 sont considérés comme volatile. Tous les autres registres sont non volatiles. L’utilisation des registres est documentée en détail dans [inscrire Usage](../build/register-usage.md) et [appelant/appelé enregistré inscrit](../build/caller-callee-saved-registers.md).  
  
 L’appelant est responsable de l’allocation d’espace pour les paramètres vers l’appelé et doit toujours allouer suffisamment d’espace pour stocker les quatre paramètres de Registre, même si l’appelé ne prend pas autant de paramètres. Cela simplifie la prise en charge pour les fonctions non prototypées en langage C et les fonctions vararg C/C++. Pour les fonctions vararg ou non prototypées, tout en virgule flottante, les valeurs doivent être dupliquées dans le Registre à usage général correspondant. Tous les paramètres au-delà des quatre premiers doivent être stockés dans la pile, au-dessus de la banque de clichés instantanés pour les quatre premières, avant l’appel. Vous trouverez les détails de la fonction vararg dans [Varargs](../build/varargs.md). Informations sur les fonctions non prototypées sont détaillées dans [fonctions non prototypées](../build/unprototyped-functions.md).  
  
## <a name="alignment"></a>Alignement  
 La plupart des structures sont alignées sur leur alignement naturel. Les principales exceptions sont le pointeur de pile et `malloc` ou `alloca` mémoire, ce qui est aligné sur 16 octets pour de meilleures performances. Alignement supérieur à 16 octets doit être effectué manuellement, mais puisque 16 octets est une taille d’alignement courante pour les opérations XMM, cela devrait fonctionner pour la plupart du code. Pour plus d’informations sur la disposition de la structure et l’alignement, consultez [Types et stockage](../build/types-and-storage.md). Pour plus d’informations sur la disposition de la pile, consultez [utilisation de la pile](../build/stack-usage.md).  
  
## <a name="unwindability"></a>Capacité de déroulement  
 Fonctions de feuille sont des fonctions qui ne modifient pas les registres non volatils. Une fonction non terminaux peut changer non volatile RSP, par exemple, en appelant une fonction ou de l’allocation d’espace de pile supplémentaires pour les variables locales. Pour récupérer les registres non volatils lorsqu’une exception est gérée, les fonctions non terminaux doivent être annotées avec les données statiques qui décrit la procédure dérouler correctement la fonction à une instruction arbitraire. Ces données sont stockées en tant que *pdata*, ou les données de la procédure, qui à son tour fait référence à *xdata*, les données de gestion des exceptions. Le xdata contient les informations de déroulement et peut pointer vers pdata supplémentaire ou une fonction de gestionnaire d’exception. Les prologues et épilogues sont extrêmement limitées afin qu’ils peuvent être décrits correctement dans xdata. Le pointeur de pile doit être aligné sur n’importe quelle région de code qui ne fait pas partie d’un épilogue ou d’un prologue, sauf dans les fonctions de feuille de 16 octets. Les fonctions terminales peuvent être vidées simplement en simulant un retour, pdata et xdata ne sont pas requis. Pour plus d’informations sur la structure appropriée des prologues de fonction et les épilogues, consultez [prologue et épilogue](../build/prolog-and-epilog.md). Pour plus d’informations sur la gestion des exceptions et la gestion des exceptions et le déroulement des pdata et xdata, consultez [(x64) gestion des exceptions](../build/exception-handling-x64.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Conventions des logiciels x64](../build/x64-software-conventions.md)