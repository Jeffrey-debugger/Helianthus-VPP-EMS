# Helianthus-VPP-EMS
https://claude.ai/public/artifacts/e10f2d6a-55fa-48d1-8a62-dffc4fd4a83c
import React, { useState } from 'react';
import { 
  Zap, Sun, Battery, TrendingUp, DollarSign, Leaf, 
  BarChart3, FileText, AlertTriangle, Activity,
  ArrowUpRight, Users, Bell, Download
} from 'lucide-react';

export default function VPPDashboard() {
  const [activeTab, setActiveTab] = useState('overview');

  const tabs = [
    { id: 'overview', name: '대시보드', icon: BarChart3 },
    { id: 'prediction', name: 'AI 예측', icon: TrendingUp },
    { id: 'ess', name: 'ESS 제어', icon: Battery },
    { id: 'dr', name: '수요반응', icon: Activity },
    { id: 'trading', name: '전력중개', icon: DollarSign },
    { id: 're100', name: 'RE100', icon: Leaf },
    { id: 'carbon', name: '탄소배출', icon: Leaf },
    { id: 'reports', name: '리포트', icon: FileText }
  ];

  return (
    <div className="min-h-screen bg-gray-50">
      <header className="bg-white shadow-sm border-b">
        <div className="max-w-7xl mx-auto px-6 py-4">
          <div className="flex items-center justify-between">
            <div className="flex items-center gap-3">
              <div className="bg-gradient-to-br from-yellow-400 to-orange-500 p-2 rounded-lg">
                <Sun className="text-white" size={28} />
              </div>
              <div>
                <h1 className="text-2xl font-bold text-gray-800">Solar Mobility VPP/EMS</h1>
                <p className="text-sm text-gray-500">통합 에너지 관리 시스템</p>
              </div>
            </div>
            <div className="flex items-center gap-4">
              <button className="relative p-2 hover:bg-gray-100 rounded-lg">
                <Bell size={20} className="text-gray-600" />
                <span className="absolute top-1 right-1 w-2 h-2 bg-red-500 rounded-full"></span>
              </button>
              <div className="flex items-center gap-2 bg-gray-100 px-4 py-2 rounded-lg">
                <Users size={20} className="text-gray-600" />
                <span className="text-sm font-medium">관리자</span>
              </div>
            </div>
          </div>
        </div>
      </header>

      <nav className="bg-white border-b sticky top-0 z-10">
        <div className="max-w-7xl mx-auto px-6">
          <div className="flex gap-1 overflow-x-auto">
            {tabs.map(tab => {
              const Icon = tab.icon;
              return (
                <button
                  key={tab.id}
                  onClick={() => setActiveTab(tab.id)}
                  className={`flex items-center gap-2 px-4 py-3 text-sm font-medium whitespace-nowrap border-b-2 transition-colors ${
                    activeTab === tab.id
                      ? 'border-orange-500 text-orange-600'
                      : 'border-transparent text-gray-600 hover:text-gray-800'
                  }`}
                >
                  <Icon size={18} />
                  {tab.name}
                </button>
              );
            })}
          </div>
        </div>
      </nav>

      <main className="max-w-7xl mx-auto px-6 py-6">
        {activeTab === 'overview' && (
          <div className="space-y-6">
            <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4">
              <div className="bg-white rounded-xl shadow-sm p-6 border">
                <div className="flex items-center justify-between mb-4">
                  <div className="bg-yellow-100 p-3 rounded-lg">
                    <Sun className="text-yellow-600" size={24} />
                  </div>
                  <span className="text-xs text-green-600 flex items-center gap-1">
                    <ArrowUpRight size={14} />
                    +12.5%
                  </span>
                </div>
                <h3 className="text-gray-600 text-sm mb-1">현재 발전량</h3>
                <p className="text-3xl font-bold text-gray-800">
                  1,247 <span className="text-lg text-gray-500">kW</span>
                </p>
              </div>

              <div className="bg-white rounded-xl shadow-sm p-6 border">
                <div className="flex items-center justify-between mb-4">
                  <div className="bg-blue-100 p-3 rounded-lg">
                    <TrendingUp className="text-blue-600" size={24} />
                  </div>
                  <span className="text-xs text-blue-600">AI 예측</span>
                </div>
                <h3 className="text-gray-600 text-sm mb-1">예상 발전량 (1h)</h3>
                <p className="text-3xl font-bold text-gray-800">
                  1,580 <span className="text-lg text-gray-500">kW</span>
                </p>
              </div>

              <div className="bg-white rounded-xl shadow-sm p-6 border">
                <div className="flex items-center justify-between mb-4">
                  <div className="bg-green-100 p-3 rounded-lg">
                    <Battery className="text-green-600" size={24} />
                  </div>
                  <span className="text-xs text-gray-600">78%</span>
                </div>
                <h3 className="text-gray-600 text-sm mb-1">ESS 충전률</h3>
                <p className="text-3xl font-bold text-gray-800">
                  2.5 <span className="text-lg text-gray-500">MWh</span>
                </p>
              </div>

              <div className="bg-white rounded-xl shadow-sm p-6 border">
                <div className="flex items-center justify-between mb-4">
                  <div className="bg-purple-100 p-3 rounded-lg">
                    <Activity className="text-purple-600" size={24} />
                  </div>
                  <span className="text-xs text-green-600">-8.2%</span>
                </div>
                <h3 className="text-gray-600 text-sm mb-1">DR 절감량</h3>
                <p className="text-3xl font-bold text-gray-800">
                  320 <span className="text-lg text-gray-500">kW</span>
                </p>
              </div>
            </div>

            <div className="bg-white rounded-xl shadow-sm p-6 border">
              <h2 className="text-lg font-bold text-gray-800 mb-4">이동형 충전차량 현황</h2>
              <div className="grid grid-cols-1 md:grid-cols-4 gap-4">
                {[
                  { id: 1, location: '원주시', battery: 85, status: '대기' },
                  { id: 2, location: '횡성군', battery: 92, status: '충전중' },
                  { id: 3, location: '강릉시', battery: 67, status: '이동중' },
                  { id: 4, location: '춘천시', battery: 78, status: '대기' }
                ].map(vehicle => (
                  <div key={vehicle.id} className="border rounded-lg p-4">
                    <div className="flex items-center justify-between mb-3">
                      <span className="font-bold">차량 #{vehicle.id}</span>
                      <span className={`text-xs px-2 py-1 rounded-full ${
                        vehicle.status === '충전중' ? 'bg-green-100 text-green-700' :
                        vehicle.status === '이동중' ? 'bg-blue-100 text-blue-700' :
                        'bg-gray-100 text-gray-700'
                      }`}>
                        {vehicle.status}
                      </span>
                    </div>
                    <div className="space-y-2 text-sm">
                      <div className="flex justify-between">
                        <span className="text-gray-600">위치</span>
                        <span className="font-medium">{vehicle.location}</span>
                      </div>
                      <div className="flex justify-between">
                        <span className="text-gray-600">배터리</span>
                        <span className="font-medium">{vehicle.battery}%</span>
                      </div>
                    </div>
                  </div>
                ))}
              </div>
            </div>

            <div className="grid grid-cols-1 lg:grid-cols-2 gap-6">
              <div className="bg-white rounded-xl shadow-sm p-6 border">
                <h3 className="text-lg font-bold mb-4">실시간 발전량 추이</h3>
                <div className="h-64 flex items-end justify-between gap-2">
                  {[65, 78, 82, 75, 88, 92, 85, 90, 95, 88, 92, 100].map((height, i) => (
                    <div 
                      key={i} 
                      className="flex-1 bg-gradient-to-t from-yellow-400 to-orange-500 rounded-t" 
                      style={{ height: `${height}%` }}
                    ></div>
                  ))}
                </div>
              </div>

              <div className="bg-white rounded-xl shadow-sm p-6 border">
                <h3 className="text-lg font-bold mb-4">에너지 믹스</h3>
                <div className="flex items-center justify-center h-64">
                  <div className="text-center">
                    <div className="text-6xl font-bold text-green-600 mb-2">100%</div>
                    <div className="text-gray-600">재생에너지</div>
                    <div className="mt-4 space-y-2">
                      <div className="flex items-center gap-2 text-sm">
                        <div className="w-3 h-3 bg-yellow-400 rounded-full"></div>
                        <span>태양광 75%</span>
                      </div>
                      <div className="flex items-center gap-2 text-sm">
                        <div className="w-3 h-3 bg-green-400 rounded-full"></div>
                        <span>ESS 20%</span>
                      </div>
                      <div className="flex items-center gap-2 text-sm">
                        <div className="w-3 h-3 bg-blue-400 rounded-full"></div>
                        <span>기타 5%</span>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        )}

        {activeTab === 'prediction' && (
          <div className="bg-white rounded-xl shadow-sm p-6 border">
            <h2 className="text-xl font-bold mb-6">AI 기반 발전량 예측</h2>
            <div className="grid grid-cols-3 gap-4 mb-6">
              <div className="bg-blue-50 rounded-lg p-4">
                <p className="text-sm text-blue-600 mb-1">단기 예측 (1시간)</p>
                <p className="text-2xl font-bold text-blue-900">1,580 kW</p>
                <p className="text-xs text-blue-700 mt-1">신뢰도: 94%</p>
              </div>
              <div className="bg-green-50 rounded-lg p-4">
                <p className="text-sm text-green-600 mb-1">중기 예측 (24시간)</p>
                <p className="text-2xl font-bold text-green-900">28.5 MWh</p>
                <p className="text-xs text-green-700 mt-1">신뢰도: 87%</p>
              </div>
              <div className="bg-purple-50 rounded-lg p-4">
                <p className="text-sm text-purple-600 mb-1">장기 예측 (7일)</p>
                <p className="text-2xl font-bold text-purple-900">198 MWh</p>
                <p className="text-xs text-purple-700 mt-1">신뢰도: 78%</p>
              </div>
            </div>
            <div className="bg-gray-50 rounded-lg p-6">
              <h3 className="font-bold mb-4">주간 발전량 예측</h3>
              <div className="h-64 flex items-end gap-3">
                {['월', '화', '수', '목', '금', '토', '일'].map((day, i) => (
                  <div key={i} className="flex-1 flex flex-col items-center gap-2">
                    <div 
                      className="w-full bg-green-400 rounded-t" 
                      style={{ height: `${70 + i * 5}%` }}
                    ></div>
                    <span className="text-xs">{day}</span>
                  </div>
                ))}
              </div>
            </div>
          </div>
        )}

        {activeTab === 'ess' && (
          <div className="bg-white rounded-xl shadow-sm p-6 border">
            <h2 className="text-xl font-bold mb-6">ESS 연계 제어</h2>
            <div className="grid grid-cols-2 gap-6 mb-6">
              <div className="bg-green-50 rounded-lg p-6">
                <h3 className="font-bold mb-4">ESS 충전 상태</h3>
                <div className="bg-gray-200 rounded-full h-4 mb-2">
                  <div className="bg-green-600 h-4 rounded-full" style={{ width: '78%' }}></div>
                </div>
                <p className="text-sm text-gray-600">충전률: 78%</p>
              </div>
              <div className="bg-blue-50 rounded-lg p-6">
                <h3 className="font-bold mb-4">자동 제어</h3>
                <div className="space-y-2 text-sm">
                  <div className="flex justify-between">
                    <span>피크시간 방전</span>
                    <span className="text-green-600 font-bold">ON</span>
                  </div>
                  <div className="flex justify-between">
                    <span>심야시간 충전</span>
                    <span className="text-green-600 font-bold">ON</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        )}

        {activeTab === 'dr' && (
          <div className="bg-white rounded-xl shadow-sm p-6 border">
            <h2 className="text-xl font-bold mb-6">수요반응(DR) 관리</h2>
            <div className="grid grid-cols-3 gap-4 mb-6">
              <div className="bg-purple-50 rounded-lg p-4">
                <p className="text-sm text-purple-600">오늘 절감량</p>
                <p className="text-2xl font-bold text-purple-900">320 kW</p>
              </div>
              <div className="bg-blue-50 rounded-lg p-4">
                <p className="text-sm text-blue-600">이번 달 절감</p>
                <p className="text-2xl font-bold text-blue-900">8.5 MWh</p>
              </div>
              <div className="bg-green-50 rounded-lg p-4">
                <p className="text-sm text-green-600">DR 참여율</p>
                <p className="text-2xl font-bold text-green-900">94%</p>
              </div>
            </div>
            <div className="bg-yellow-50 border border-yellow-200 rounded-lg p-4">
              <div className="flex items-start gap-3">
                <AlertTriangle className="text-yellow-600" size={24} />
                <div>
                  <h3 className="font-bold text-yellow-800">피크 시간대 DR 이벤트</h3>
                  <p className="text-sm text-yellow-700">오늘 14:00-16:00 전력 감축 요청</p>
                </div>
              </div>
            </div>
          </div>
        )}

        {activeTab === 'trading' && (
          <div className="bg-white rounded-xl shadow-sm p-6 border">
            <h2 className="text-xl font-bold mb-6">실시간 전력 중개</h2>
            <div className="grid grid-cols-4 gap-4 mb-6">
              <div className="bg-blue-50 rounded-lg p-4">
                <p className="text-sm text-blue-600">현재 SMP</p>
                <p className="text-2xl font-bold text-blue-900">127.5원</p>
              </div>
              <div className="bg-green-50 rounded-lg p-4">
                <p className="text-sm text-green-600">오늘 거래량</p>
                <p className="text-2xl font-bold text-green-900">1.2 MWh</p>
              </div>
              <div className="bg-purple-50 rounded-lg p-4">
                <p className="text-sm text-purple-600">거래 수익</p>
                <p className="text-2xl font-bold text-purple-900">153천원</p>
              </div>
              <div className="bg-orange-50 rounded-lg p-4">
                <p className="text-sm text-orange-600">REC 가격</p>
                <p className="text-2xl font-bold text-orange-900">48,500원</p>
              </div>
            </div>
          </div>
        )}

        {activeTab === 're100' && (
          <div className="bg-white rounded-xl shadow-sm p-6 border">
            <h2 className="text-xl font-bold mb-6">RE100 관리</h2>
            <div className="grid grid-cols-2 gap-6 mb-6">
              <div className="bg-green-50 rounded-lg p-6">
                <h3 className="font-bold mb-4">RE100 달성률</h3>
                <div className="text-center">
                  <p className="text-5xl font-bold text-green-600 mb-2">100%</p>
                  <p className="text-sm text-gray-600">목표 달성</p>
                </div>
              </div>
              <div className="bg-blue-50 rounded-lg p-6">
                <h3 className="font-bold mb-4">재생에너지 사용량</h3>
                <div className="space-y-2 text-sm">
                  <div className="flex justify-between">
                    <span>이번 달</span>
                    <span className="font-bold">125 MWh</span>
                  </div>
                  <div className="flex justify-between">
                    <span>올해 누적</span>
                    <span className="font-bold">1,450 MWh</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        )}

        {activeTab === 'carbon' && (
          <div className="bg-white rounded-xl shadow-sm p-6 border">
            <h2 className="text-xl font-bold mb-6">탄소배출 관리</h2>
            <div className="grid grid-cols-3 gap-4 mb-6">
              <div className="bg-green-50 rounded-lg p-4">
                <p className="text-sm text-green-600">탄소 감축량</p>
                <p className="text-2xl font-bold text-green-900">458톤</p>
                <p className="text-xs text-green-700 mt-1">올해 누적</p>
              </div>
              <div className="bg-blue-50 rounded-lg p-4">
                <p className="text-sm text-blue-600">배출권 보유</p>
                <p className="text-2xl font-bold text-blue-900">1,250톤</p>
                <p className="text-xs text-blue-700 mt-1">거래 가능</p>
              </div>
              <div className="bg-purple-50 rounded-lg p-4">
                <p className="text-sm text-purple-600">예상 수익</p>
                <p className="text-2xl font-bold text-purple-900">25백만원</p>
                <p className="text-xs text-purple-700 mt-1">배출권 거래</p>
              </div>
            </div>
            <div className="bg-gray-50 rounded-lg p-6">
              <h3 className="font-bold mb-4">월별 탄소 감축 추이</h3>
              <div className="h-48 flex items-end gap-2">
                {[45, 52, 48, 55, 58, 62, 65, 58, 63, 68, 72, 75].map((height, i) => (
                  <div 
                    key={i} 
                    className="flex-1 bg-green-500 rounded-t" 
                    style={{ height: `${height}%` }}
                  ></div>
                ))}
              </div>
            </div>
          </div>
        )}

        {activeTab === 'reports' && (
          <div className="bg-white rounded-xl shadow-sm p-6 border">
            <div className="flex items-center justify-between mb-6">
              <h2 className="text-xl font-bold">리포트 생성</h2>
              <button className="flex items-center gap-2 px-4 py-2 bg-blue-500 text-white rounded-lg hover:bg-blue-600">
                <Download size={18} />
                전체 다운로드
              </button>
            </div>
            <div className="space-y-3">
              {[
                { name: '월간 에너지 리포트', date: '2025-10', size: '2.5MB' },
                { name: 'RE100 달성 보고서', date: '2025-10', size: '1.8MB' },
                { name: '탄소배출 인벤토리', date: '2025-10', size: '3.2MB' },
                { name: 'DR 참여 실적', date: '2025-10', size: '1.2MB' },
                { name: '전력거래 수익 분석', date: '2025-10', size: '2.1MB' }
              ].map((report, i) => (
                <div key={i} className="flex items-center justify-between p-4 border rounded-lg hover:bg-gray-50">
                  <div className="flex items-center gap-3">
                    <FileText className="text-gray-400" size={24} />
                    <div>
                      <p className="font-medium">{report.name}</p>
                      <p className="text-sm text-gray-500">{report.date} · {report.size}</p>
                    </div>
                  </div>
                  <button className="px-4 py-2 text-sm bg-gray-100 rounded-lg hover:bg-gray-200">
                    다운로드
                  </button>
                </div>
              ))}
            </div>
          </div>
        )}
      </main>
    </div>
  );
}
