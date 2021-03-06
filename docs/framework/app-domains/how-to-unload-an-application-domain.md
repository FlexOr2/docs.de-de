---
title: 'Gewusst wie: Entladen einer Anwendungsdomäne'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8b4cbdff72167cfc063254cf5370d22fb729b0a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2018
ms.locfileid: "50088571"
---
# <a name="how-to-unload-an-application-domain"></a>Gewusst wie: Entladen einer Anwendungsdomäne
Wenn Sie die Nutzung einer Anwendungsdomäne beenden möchten, entladen Sie sie mithilfe der <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType>-Methode. Durch die **Unload**-Methode wird die angegebene Anwendungsdomäne ordnungsgemäß geschlossen. Während des Entladevorgangs können keine neuen Threads auf die Anwendungsdomäne zugreifen. Alle anwendungsdomänenspezifischen Strukturen werden freigegeben.  
  
 In die Anwendungsdomäne geladene Assemblys werden entfernt und sind nicht weiter verfügbar. Wenn eine in der Anwendungsdomäne enthaltene Assembly domänenneutral ist, verbleiben deren Daten im Speicher, bis der gesamte Prozess beendet wird. Das Beenden des gesamten Prozesses ist die einzige Möglichkeit, eine domänenneutrale Assembly zu entladen. Mitunter kann es vorkommen, dass das Entladen einer Anwendungsdomäne nicht erfolgreich ist und zu einer <xref:System.CannotUnloadAppDomainException> führt.  
  
 Im folgenden Codebeispiel wird eine neue Anwendungsdomäne mit dem Namen `MyDomain` erstellt, und es werden einige Informationen auf der Konsole ausgegeben. Anschließend wird die Anwendungsdomäne entladen. Beachten Sie, dass danach der Versuch gestartet wird, den angezeigten Namen der entladenen Anwendungsdomäne auf der Konsole auszugeben. Dadurch wird eine Ausnahme generiert, die von den „try/catch“-Anweisungen am Ende des Programms abgefangen wird.  
  
## <a name="example"></a>Beispiel  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Siehe auch  
- [Programming with Application Domains (Programmieren mit Anwendungsdomänen)](application-domains.md#programming-with-application-domains)  
- [Gewusst wie: Erstellen einer Anwendungsdomäne](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
- [Verwenden von Anwendungsdomänen](../../../docs/framework/app-domains/use.md)
