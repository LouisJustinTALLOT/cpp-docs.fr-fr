---
title: __identifier (c + c++ / CLI) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- __identifier
- __identifier_cpp
dev_langs:
- C++
helpviewer_keywords:
- __identifier keyword [C++]
ms.assetid: 348428af-afa7-4ff3-b571-acf874301cf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a96363fcfbc753e727c6cbb6a5efbbb5606b6c40
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877681"
---
# <a name="identifier-ccli"></a>__identifier (C++/CLI)
Permet l’utilisation de mots clés Visual C++ en tant qu’identificateurs.  
  
## <a name="all-platforms"></a>Toutes les plateformes  
**Syntaxe**  
  
```  
__identifier(  
Visual_C++_keyword  
)  
  
```  
  
**Remarques**  
  
Utilisation de la `__identifier` mot clé pour les identificateurs qui ne sont pas des mots clés est autorisée, mais fortement déconseillée en termes de style.  
  
## <a name="windows-runtime"></a>Windows Runtime  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/ZW**  
  
### <a name="examples"></a>Exemples  
 **Exemple**  
  
 Dans l’exemple suivant, une classe nommée `template` est créé en c# et distribué en tant que DLL. Dans le programme Visual C++ qui utilise le `template` (classe), le `__identifier` mot clé masque le fait que `template` est un mot clé C++ standard.  
  
```  
// identifier_template.cs  
// compile with: /target:library  
public class template {  
   public void Run() { }  
}  
```  
  
```  
// keyword__identifier.cpp  
// compile with: /ZW  
#using <identifier_template.dll>  
int main() {  
   __identifier(template)^ pTemplate = ref new __identifier(template)();  
   pTemplate->Run();  
}  
```  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 **Remarques**  
  
 Le `__identifier` mot clé est valide avec le **/CLR** option du compilateur.  
  
### <a name="requirements"></a>Spécifications  
 Option du compilateur : **/clr**  
  
### <a name="examples"></a>Exemples  
 **Exemple**  
  
 Dans l’exemple suivant, une classe nommée `template` est créé en c# et distribué en tant que DLL. Dans le programme Visual C++ qui utilise le `template` (classe), le `__identifier` mot clé masque le fait que `template` est un mot clé C++ standard.  
  
```  
// identifier_template.cs  
// compile with: /target:library  
public class template {  
   public void Run() { }  
}  
```  
  
```  
// keyword__identifier.cpp  
// compile with: /clr  
#using <identifier_template.dll>  
  
int main() {  
   __identifier(template) ^pTemplate = gcnew __identifier(template)();  
   pTemplate->Run();  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)   
 [Extensions de composant pour les plateformes Runtime](../windows/component-extensions-for-runtime-platforms.md)