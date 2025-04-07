# CRM-A4MD
// CRM base para gerenciamento de clientes e links
import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Input } from "@/components/ui/input";
import { Button } from "@/components/ui/button";
import { Plus, LinkIcon } from "lucide-react";

export default function CRMClientesLinks() {
  const [clientes, setClientes] = useState([]);
  const [nome, setNome] = useState("");
  const [link, setLink] = useState("");

  const adicionarCliente = () => {
    if (nome && link) {
      setClientes([...clientes, { nome, link }]);
      setNome("");
      setLink("");
    }
  };

  return (
    <div className="min-h-screen bg-gray-100 p-6">
      <h1 className="text-3xl font-bold mb-6 text-center">CRM A4MD</h1>

      <div className="grid grid-cols-1 sm:grid-cols-3 gap-4 mb-6">
        <Input
          placeholder="Nome do Cliente"
          value={nome}
          onChange={(e) => setNome(e.target.value)}
        />
        <Input
          placeholder="Link da Página"
          value={link}
          onChange={(e) => setLink(e.target.value)}
        />
        <Button onClick={adicionarCliente} className="w-full sm:w-auto">
          <Plus className="mr-2 h-4 w-4" /> Adicionar
        </Button>
      </div>

      <div className="grid gap-4 md:grid-cols-2 lg:grid-cols-3">
        {clientes.map((cliente, index) => (
          <Card key={index} className="bg-white shadow-md">
            <CardContent className="p-4">
              <h2 className="text-xl font-semibold mb-2">{cliente.nome}</h2>
              <a
                href={cliente.link}
                target="_blank"
                rel="noopener noreferrer"
                className="text-blue-600 underline flex items-center"
              >
                <LinkIcon className="mr-2 w-4 h-4" /> Ver Link
              </a>
            </CardContent>
          </Card>
        ))}
      </div>
    </div>
  );
}
