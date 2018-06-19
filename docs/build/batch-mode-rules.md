---
title: Les règles en Mode Batch | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inference rules in NMAKE
- NMAKE program, inference rules
- batch-mode inference rules in NMAKE
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2b002b17fcc70ff4e374fb0630e9c18a52cbfc4f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361442"
---
# <a name="batch-mode-rules"></a>Règles en mode batch
```  
{frompath}.fromext{topath}.toext::  
   commands  
```  
  
 Règles d’inférence en mode batch ne fournissent qu’un seul appel de la règle d’inférence quand N commandes passent par cette règle d’inférence. Sans règles d’inférence en mode batch, il faudrait N commandes à appeler. N est le nombre de personnes qui déclenchent la règle d’inférence.  
  
 Les makefiles contenant des règles d’inférence en mode batch doivent utiliser NMAKE version 1.62 ou ultérieure. Pour vérifier la version NMAKE, exécutez la macro _NMAKE_VER fournie avec NMAKE version 1.62 ou ultérieure. Cette macro retourne une chaîne représentant la version du produit Visual C++.  
  
 La différence syntaxique uniquement à partir de la règle d’inférence standard est que la règle d’inférence en mode batch se termine par un double deux-points ( :).  
  
> [!NOTE]
>  L’outil appelé doit être en mesure de gérer plusieurs fichiers. La règle d’inférence en mode batch doit utiliser `$<` comme macro pour accéder aux fichiers dépendants.  
  
 Les règles d’inférence en mode batch peuvent accélérer le processus de génération. Il est plus rapide pour fournir des fichiers au compilateur en batch, car le pilote du compilateur est appelé une seule fois. Par exemple, le compilateur C et C++ plus performant lors du traitement d’un ensemble de fichiers, car elle peut rester résident pendant le processus en mémoire.  
  
 L’exemple suivant montre comment utiliser les règles d’inférence en mode batch :  
  
```  
#  
# sample makefile to illustrate batch-mode inference rules  
#  
O = .  
S = .  
Objs = $O/foo1.obj $O/foo2.obj $O/foo2.obj $O/foo3.obj $O/foo4.obj  
CFLAGS = -nologo  
  
all : $(Objs)  
  
!ifdef NOBatch  
{$S}.cpp{$O}.obj:  
!else  
{$S}.cpp{$O}.obj::  
!endif  
   $(CC) $(CFLAGS) -Fd$O\ -c $<  
  
$(Objs) :  
  
#end of makefile  
```  
  
 NMAKE génère la sortie suivante sans règles d’inférence en mode batch :  
  
```  
E:\tmp> nmake -f test.mak -a NOBatch=1  
  
Microsoft (R) Program Maintenance Utility   Version 7.00.0000  
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.  
        cl -nologo -Fd.\ -c .\foo1.cpp  
foo1.cpp  
        cl -nologo -Fd.\ -c .\foo2.cpp  
foo2.cpp  
        cl -nologo -Fd.\ -c .\foo3.cpp  
foo3.cpp  
        cl -nologo -Fd.\ -c .\foo4.cpp  
foo4.cpp  
```  
  
 NMAKE génère le résultat suivant avec les règles d’inférence en mode batch :  
  
```  
E:\tmp> nmake -f test.mak -a  
  
Microsoft (R) Program Maintenance Utility   Version 7.00.0000  
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.  
  
        cl -nologo -Fd.\ -c .\foo1.cpp .\foo2.cpp .\foo3.cpp .\foo4.cpp  
foo1.cpp  
foo2.cpp  
foo3.cpp  
foo4.cpp  
Generating Code...  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Règles d’inférence](../build/inference-rules.md)