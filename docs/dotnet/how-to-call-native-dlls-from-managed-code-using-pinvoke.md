---
title: 'Procédure : Appeler des DLL natives à partir du Code managé à l’aide de PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- platform invoke [C++], calling native DLLs
- interop [C++], calling native DLLs
- marshaling [C++], calling native DLLs
- data marshaling [C++], calling native DLLs
ms.assetid: 3273eb4b-38d1-4619-92a6-71bda542be72
ms.openlocfilehash: e51e094cc013250fc254a09e279745f1f9c108ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222809"
---
# <a name="how-to-call-native-dlls-from-managed-code-using-pinvoke"></a>Procédure : Appeler des DLL natives à partir du Code managé à l’aide de PInvoke

Les fonctions qui sont implémentées dans des DLL non managées peuvent être appelées à partir du code managé à l’aide de la fonctionnalité Platform Invoke (P/Invoke). Si le code source pour la DLL n’est pas disponible, P/Invoke est la seule option pour l’interopérabilité. Toutefois, contrairement à d’autres langages .NET, Visual C++ fournit une alternative à P/Invoke. Pour plus d’informations, consultez [à l’aide du interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

## <a name="example"></a>Exemple

L’exemple de code suivant utilise Win32 [GetSystemMetrics](/windows/desktop/api/winuser/nf-winuser-getsystemmetrics) fonction pour récupérer la résolution actuelle de l’écran en pixels.

Pour les fonctions qui utilisent uniquement des types intrinsèques comme arguments et valeurs de retour, aucun travail supplémentaire n’est nécessaire. Autres types de données, telles que les pointeurs de fonction, les tableaux et les structures, requièrent des attributs supplémentaires pour garantir le marshaling de données appropriées.

Il n’est pas obligatoire, il est recommandé d’effectuer des membres statiques de déclarations P/Invoke d’une classe value afin qu’ils n’existent pas dans l’espace de noms global, comme illustré dans cet exemple.

```
// pinvoke_basic.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value class Win32 {
public:
   [DllImport("User32.dll")]
   static int GetSystemMetrics(int);

   enum class SystemMetricIndex {
      // Same values as those defined in winuser.h.
      SM_CXSCREEN = 0,
      SM_CYSCREEN = 1
   };
};

int main() {
   int hRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CXSCREEN) );
   int vRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CYSCREEN) );
   Console::WriteLine("screen resolution: {0},{1}", hRes, vRes);
}
```

## <a name="see-also"></a>Voir aussi

[Utilisation d’un PInvoke explicite en C++ (attribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
