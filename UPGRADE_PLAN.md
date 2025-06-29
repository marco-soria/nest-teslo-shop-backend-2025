# Plan de Actualización - Node.js 22 Compatibility

## Estado Actual ✅
- Node.js: v22.14.0 
- Bcrypt: v6.0.0 (✅ Resuelto)
- Multer: v2.0.1 (✅ Resuelto)

## Prioridades de Actualización

### 🔴 CRÍTICO - Actualizar INMEDIATAMENTE
```bash
# Vulnerabilidad de seguridad
pnpm update @nestjs/serve-static
```

### 🟡 MEDIO - Actualizar por GRUPOS (sin romper funcionamiento)

#### Grupo 1: TypeScript y Tooling
```bash
pnpm update @types/node
pnpm update typescript
pnpm update ts-jest
```

#### Grupo 2: Testing Framework
```bash
pnpm update jest
pnpm update @types/jest
pnpm update supertest
```

#### Grupo 3: NestJS Core (CUIDADO - puede romper APIs)
```bash
# Solo si es necesario - requiere revisar breaking changes
pnpm update @nestjs/common @nestjs/core
pnpm update @nestjs/platform-express
```

### 🟢 BAJO - Opcional
```bash
pnpm update uuid @types/uuid
pnpm update rimraf
```

## Librerías que NO tocar por ahora:
- ESLint (v8 → v9 tiene breaking changes)
- NestJS suite completa (v10 → v11 tiene breaking changes)

## Estrategia Recomendada:

1. **Actualizar una librería a la vez**
2. **Probar después de cada actualización**
3. **Hacer commit después de cada grupo exitoso**
4. **Tener un rollback plan**

## Comandos de Test después de cada actualización:
```bash
pnpm run build
pnpm run test
pnpm run start:dev
```

## Node.js Compatibility Matrix:
- Node 18: ✅ Todas las versiones actuales
- Node 20: ✅ Todas las versiones actuales  
- Node 22: ✅ Requiere actualizar algunas dependencias (en progreso)

## Librerías con binarios nativos (requieren rebuild si fallan):
- bcrypt ✅ (ya resuelto)
- pg (PostgreSQL driver) - monitorear
- multer ✅ (ya resuelto)
