## API Report File for "@fluidframework/ink"

> Do not edit this file. It is a report generated by [API Extractor](https://api-extractor.com/).

```ts

import { IChannelAttributes } from '@fluidframework/datastore-definitions';
import { IChannelFactory } from '@fluidframework/datastore-definitions';
import { IChannelServices } from '@fluidframework/datastore-definitions';
import { IChannelStorageService } from '@fluidframework/datastore-definitions';
import { IFluidDataStoreRuntime } from '@fluidframework/datastore-definitions';
import { IFluidSerializer } from '@fluidframework/core-interfaces';
import { ISequencedDocumentMessage } from '@fluidframework/protocol-definitions';
import { ISharedObject } from '@fluidframework/shared-object-base';
import { ISharedObjectEvents } from '@fluidframework/shared-object-base';
import { ITree } from '@fluidframework/protocol-definitions';
import { SharedObject } from '@fluidframework/shared-object-base';

// @public
export interface IClearOperation {
    time: number;
    type: "clear";
}

// @public
export interface IColor {
    a: number;
    b: number;
    g: number;
    r: number;
}

// @public
export interface ICreateStrokeOperation {
    id: string;
    pen: IPen;
    time: number;
    type: "createStroke";
}

// @public
export interface IInk extends ISharedObject<IInkEvents> {
    appendPointToStroke(point: IInkPoint, id: string): IInkStroke;
    clear(): void;
    createStroke(pen: IPen): IInkStroke;
    getStroke(key: string): IInkStroke;
    getStrokes(): IInkStroke[];
}

// @public (undocumented)
export interface IInkEvents extends ISharedObjectEvents {
    // (undocumented)
    (event: "stylus", listener: (operation: IStylusOperation) => void): any;
    // (undocumented)
    (event: "clear", listener: () => void): any;
}

// @public
export type IInkOperation = IClearOperation | ICreateStrokeOperation | IStylusOperation;

// @public
export interface IInkPoint {
    pressure: number;
    time: number;
    x: number;
    y: number;
}

// @public
export interface IInkStroke {
    id: string;
    pen: IPen;
    points: IInkPoint[];
}

// @public @sealed
export class Ink extends SharedObject<IInkEvents> implements IInk {
    constructor(runtime: IFluidDataStoreRuntime, id: string, attributes: IChannelAttributes);
    appendPointToStroke(point: IInkPoint, id: string): IInkStroke;
    // (undocumented)
    protected applyStashedOp(): void;
    clear(): void;
    static create(runtime: IFluidDataStoreRuntime, id?: string): Ink;
    createStroke(pen: IPen): IInkStroke;
    static getFactory(): InkFactory;
    getStroke(key: string): IInkStroke;
    getStrokes(): IInkStroke[];
    // (undocumented)
    protected loadCore(storage: IChannelStorageService): Promise<void>;
    // (undocumented)
    protected onDisconnect(): void;
    // (undocumented)
    protected processCore(message: ISequencedDocumentMessage, local: boolean, localOpMetadata: unknown): void;
    // (undocumented)
    protected registerCore(): void;
    // (undocumented)
    protected snapshotCore(serializer: IFluidSerializer): ITree;
}

// @public (undocumented)
export class InkCanvas {
    constructor(canvas: HTMLCanvasElement, model: IInk);
    // (undocumented)
    clear(): void;
    // (undocumented)
    replay(): void;
    // (undocumented)
    setPenColor(color: IColor): void;
    // (undocumented)
    sizeCanvasBackingStore(): void;
}

// @public @sealed
export class InkFactory implements IChannelFactory {
    // (undocumented)
    static readonly Attributes: IChannelAttributes;
    // (undocumented)
    get attributes(): IChannelAttributes;
    // (undocumented)
    create(runtime: IFluidDataStoreRuntime, id: string): ISharedObject;
    // (undocumented)
    load(runtime: IFluidDataStoreRuntime, id: string, services: IChannelServices, attributes: IChannelAttributes): Promise<ISharedObject>;
    // (undocumented)
    static Type: string;
    // (undocumented)
    get type(): string;
}

// @public
export interface IPen {
    color: IColor;
    thickness: number;
}

// @public
export interface IStylusOperation {
    id: string;
    point: IInkPoint;
    type: "stylus";
}


// (No @packageDocumentation comment for this package)

```