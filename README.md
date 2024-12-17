'use client';
import { DashboardPageLabel } from '../common';
import { Input } from '@/components/ui/input';
import { useForm } from 'react-hook-form';
import { RotatingLines } from 'react-loader-spinner';
import { useCalls } from '@/hooks/useCalls';
import { useMemo } from 'react';
import { filter, includes, isEmpty, lowerCase } from 'lodash';
import { RefreshIcon, SearchIcon } from '@/icons';
import { IDbCall } from '@/types';
import { Button } from '@/components/ui/button';
import CallLogsTable from './CallLogsTable';
import Image from 'next/image';
import './CallLogs.css';
const CallLogs = () => {
const {
callLogs,
emptyCallLogs,
fetchingCallLogs,
fetchCallLogs,
reFetchingCallLogs,
} = useCalls();
const { register, watch } = useForm();
const searchQuery = watch('search');
const filteredCallLogs = useMemo(
() =>
isEmpty(searchQuery)
? filter(callLogs)
: filter(callLogs, (log: IDbCall) => {
return includes(lowerCase(log?.from), lowerCase(searchQuery));
}),
[callLogs, searchQuery]
);
return (
<div className="relative box-border mr-5">
<span className="relative flex items-start">
<DashboardPageLabel
label="Call Logs"
description="Check your agent call logs"
/>
{!isEmpty(callLogs) && (
<Button
variant={'ghost'}
className="absolute left-[144px] top-[-7px]"
onClick={() => fetchCallLogs()}
>
{reFetchingCallLogs ? (
<RotatingLines
strokeColor="#000000"
strokeWidth="5"
animationDuration="0.75"
width="24"
visible
/>
) : (
<RefreshIcon />
)}
</Button>
)}
</span>
{emptyCallLogs && (
<div className="call-logs-empty-illustration">
<Image
width={497}
height={397}
alt="call-logs"
src="/assets/Call-Logs.png"
className="call-logs-empty-illustration-img"
/>
</div>
)}
{fetchingCallLogs && (
<div className="w-full flex justify-center items-center mt-24">
<RotatingLines
strokeColor="#000000"
strokeWidth="5"
animationDuration="0.75"
width="24"
visible
/>
</div>
)}
{!fetchingCallLogs && !emptyCallLogs && (
<>
<div className="w-full md:w-[293px] mt-5">
<Input
{...register('search')}
placeholder="Search"
className="mb-1 h-11"
rightIcon={<SearchIcon />}
/>
</div>
<CallLogsTable callLogs={filteredCallLogs} />
</>
)}
</div>
);
};
export default CallLogs;