---
title: Dépréciation des types et membres (C++ / c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: b20b01c1-a439-4ff0-8cf3-d7280c492813
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8aecb47db6e9d620ff49fac337454242a1bdb72a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605699"
---
# <a name="deprecating-types-and-members-ccx"></a>Déconseiller des types et des membres (C++/CX)
En C / c++ / CX, le fait de déconseiller des types Windows Runtime et des membres pour les producteurs et consommateurs à l’aide de la [déconseillées](http://msdn.microsoft.com/en-us/8b02ad36-3b5f-4361-888b-e6a99040e57c) attribut est pris en charge. Si vous consommez une API à laquelle cet attribut a été appliqué, vous recevez un message d'avertissement au moment de la compilation qui indique que l'API est déconseillée et recommande l'utilisation d'une autre API. Dans vos propres types et méthodes publics, vous pouvez appliquer cet attribut et fournir votre message personnalisé.  
  
> [!CAUTION]
>  Le [déconseillées](http://msdn.microsoft.com/en-us/8b02ad36-3b5f-4361-888b-e6a99040e57c) attribut doit être utilisé uniquement avec les types Windows Runtime. Pour les classes et les membres C++ standard, utilisez [__declspec(deprecated)](http://msdn.microsoft.com/library/044swk7y.aspx).  
  
### <a name="example"></a>Exemple  
 L'exemple suivant montre comment déconseiller vos propres API publiques, par exemple dans un composant Windows Runtime. Le deuxième paramètre, de type [Windows:Foundation::Metadata::DeprecationType](http://msdn.microsoft.com/en-us/ee01e63d-37d0-4273-accc-fca174f88bfa) , spécifie si l'API est déconseillée ou supprimée. Actuellement, seule la valeur DeprecationType::Deprecated est prise en charge. Le troisième paramètre de l'attribut spécifie le [Windows::Foundation::Metadata::Platform](http://msdn.microsoft.com/en-us/1eae292d-1ab7-4d97-a58c-b0beffd51ef5) auquel l'attribut s'applique.  
  
```  
  
namespace wfm = Windows::Foundation::Metadata;  
  
public ref class Bicycle sealed  
{  
  
public:  
    property double Speed;  
  
    [wfm::Deprecated("Use the Speed property to compute the angular speed of the wheel", wfm::DeprecationType::Deprecate, 0x0)]  
    double ComputeAngularVelocity();  
};  
```  
  
## <a name="supported-targets"></a>Cibles prises en charge  
 Le tableau suivant répertorie les constructions auxquelles l'attribut Deprecated peut être appliqué :  
  
||  
|-|  
|Contrôle XAML|  
|délégué|  
|événement|  
|champ enum|  
|enum|  
|struct|  
|méthode|  
|class|  
|interface|  
|propriété|  
|champ struct|  
|constructeur paramétrable|  
  
## <a name="see-also"></a>Voir aussi  
 [Système de type](../cppcx/type-system-c-cx.md)   
 [Référence du langage Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Référence des espaces de noms](../cppcx/namespaces-reference-c-cx.md)