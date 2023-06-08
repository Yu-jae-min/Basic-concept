# [pob] POB TIL-05

## # Today I Learn - 2022.05.10

### # Pre Onboarding Course

- **그립 기획서 작성** : 피그마로 개인프로젝트 그립 무비 앱 기획서를 작성하였다. but 아직 미완성...

- **그립 무비 앱 코드 리뷰** : 로켓런치 장수영님이 무비 앱 코드 리뷰를 진행해주셨다.

- **타입스크립트 연습** : 타입스크립트 적용하는 것 연습해보기

```ts
// 1
onClick?: (e: MouseEvent<HTMLButtonElement>) => void
setChecked?: (e: ChangeEvent<HTMLInputElement>) => void
onKeyDown?: (e: KeyboardEvent<HTMLInputElement>) => void
postSubmit: (e: FormEvent<HTMLFormElement>) => void

// 2
interface ButtonProps extends Omit<ButtonHTMLAttributes<unknown>, 'translate'> {
  children: string | JSX.Element | JSX.Element[]
  className?: string
  disabled?: boolean
  isSubmit?: boolean
  loading?: boolean
  name?: string
  onClick?: (e: MouseEvent<HTMLButtonElement>) => void
  btnRef?: RefObject<HTMLButtonElement>
  size: 'unset' | 'big' | 'medium' | 'small' | 'smallest'
  shape: 'unset' | 'reward' | 'rounded' | 'primary' | 'order' | 'ghost' | 'ghostLight' | 'line'
  translate?: boolean
  url?: string
  inline?: boolean
  danger?: boolean // ghost 빨간 버전
}

interface ButtonProps {
  text: string
  type:
    | 'textWithArrow'
    | 'textWithCopied'
    | 'textWithIcon'
    | 'copyButtonOnly'
    | 'iconOnly'
    | 'textOnly'
    | 'textToCopied'
  handleCopy?: () => void
}

interface Props {
  className?: string
  children: ReactNode
  asFooter?: boolean
}

// 3
interface Props {
  transactionUrl: string
  currency: string
  txId: string
  transferState: ETransferState
  arrow?: boolean
  inline?: boolean
  shape: 'line' | 'rounded'
}

export const ButtonTXID = ({
  transactionUrl,
  currency,
  txId,
  transferState,
  arrow,
  inline,
  shape,
}: Props): JSX.Element | null => {
  if (!currency || !txId) return null
  if (!isTxidAvailable(transferState)) return null

  return (
    <Button url={transactionUrl} className={styles.txidButton} shape={shape} size='unset' inline={inline}>
      <span>TX ID</span>
      {arrow ? <ArrowIcon /> : <></>}
    </Button>
  )
}

// 4
import styles, { cx } from 'styles'

import { useI18n } from 'hooks'
import Lottie from 'utils/lottie'

import LoadingAni from '@/assets/animations/loading.json'
import LoadingAniDark from '@/assets/animations/loading-dark.json'

interface Props {
  size: 'tiny' | 'small' | 'big' | 'bigger' | 'large' | 'huge'
  withLabel?: boolean
  className?: string
  forceDark?: boolean
  forceBright?: boolean
  full?: boolean
}

export const LoadingSpinner = (props: Props): JSX.Element => {
  const { size, withLabel, className, forceDark, forceBright, full } = props
  const t = useI18n()
  const wrapperClassName = cx(styles.loadingSpinner, className, styles[size], {
    [styles.forceDark]: forceDark,
    [styles.forceBright]: forceBright,
    [styles.full]: full,
  })

  return (
    <div className={wrapperClassName}>
      <Lottie animationData={LoadingAni} className={styles.brightSpinner} />
      <Lottie animationData={LoadingAniDark} className={styles.darkSpinner} />
      {withLabel && <p>{t('front:global.loading')}</p>}
    </div>
  )
}

// 5
function getActiveWidth(
  percentage: number,
  isDesktop: boolean,
  mobileMaxWidth: number,
  atTrade?: boolean,
  atWallet?: boolean
): number {
  if (atTrade) {
    const maxWidth = isDesktop ? 295 : mobileMaxWidth
    const dirtyWidth = maxWidth * percentage
    const cleanWidth = dirtyWidth - (dirtyWidth % 5) // 5의 배수로 고정
    return Math.max(cleanWidth, 5)
  }

  if (atWallet) {
    const maxWidth = isDesktop ? 480 : mobileMaxWidth
    const dirtyWidth = maxWidth * percentage
    const cleanWidth = dirtyWidth - (dirtyWidth % 8) // 8의 배수로 고정
    return Math.max(cleanWidth, 8)
  }

  return 0
}

// 6
import { Dispatch, MouseEvent, SetStateAction } from 'react'
import styles, { cx } from 'styles'

import { useI18n } from 'hooks'
import { LoadingSpinner } from '@/components/_common/LoadingSpinner'

export interface SwitchItem {
  name: string
  label?: string
  icon?: JSX.Element
  disabled?: boolean
}

interface Props<T> {
  items: SwitchItem[]
  mode: T
  setMode: (newMode: T) => void | Dispatch<SetStateAction<T>>
  className?: string
  type: 'dTag' | 'default'
  color: 'common' | 'trade' | 'setting'
  isLoading?: boolean
}

export const CommonSwitch = <T extends string>({
  items,
  mode,
  setMode,
  className,
  type,
  color,
  isLoading,
}: Props<T>): JSX.Element => {
  const t = useI18n()

  const handleMode = (e: MouseEvent<HTMLButtonElement>): void => {
    const { name } = e.currentTarget
    setMode(name as T)
  }

  const wrapperClassName = cx(styles.commonSwitch, styles[type], styles[color], className, {
    [styles.right]: mode === items[1].name,
  })

  if (isLoading) {
    return (
      <div className={wrapperClassName}>
        <LoadingSpinner size='small' forceDark />
      </div>
    )
  }

  return (
    <div className={wrapperClassName}>
      {items.map((item) => {
        return (
          <button
            key={commonSwitch-${item.name}}
            type='button'
            onClick={handleMode}
            name={item.name}
            disabled={item.disabled}
            className={cx({ [styles.active]: mode === item.name })}
            tabIndex={-1}
          >
            {item.icon || t(item.label || '')}
          </button>
        )
      })}
      <div className={styles.aniBg} />
    </div>
  )
}

// 7
import { MouseEvent } from 'react'

import DatePicker from 'react-datepicker'
import styles from 'styles'

import { SetterOrUpdater } from 'stateHooks'
import { useClickAway, useGA, useI18n, useRef, useState } from 'hooks'
import { TDateFilter } from 'types/histories.d'

import { Button } from '../_common/Button'
import DatePickerHeader from './DatePickerHeader'
import { CommonButtons } from '@/components/_common/Buttons'

interface Props {
  date: TDateFilter
  setDate: SetterOrUpdater<TDateFilter> | ((value: Date | null) => void)
  handleClose: () => void
  gaAction: string
}

const CustomDatePicker = ({ date, setDate, handleClose: handleClose2, gaAction }: Props): JSX.Element => {
  const datePickerRef = useRef<HTMLDivElement>(null)

  const { gaEvent } = useGA()
  const t = useI18n()

  const [selected, setSelected] = useState(date)

  useClickAway(datePickerRef, handleClose2)

  const renderDayContents = (day: number): JSX.Element => {
    return (
      <div>
        <span className={styles.dayContent}>{day}</span>
      </div>
    )
  }

  const handleChange = (d: Date): void => setSelected(d)

  const handleConfirm = (): void => {
    setDate(selected)
    handleClose2()
    gaEvent({ action: `${gaAction}_calendar_search` })
  }

  const handleClose = (e: MouseEvent<HTMLButtonElement>) => {
    return e
  }

// 8
  return (
    <div className={styles.datePicker} ref={datePickerRef} translate='no'>
      <DatePicker
        selected={selected}
        onChange={handleChange}
        inline
        renderDayContents={renderDayContents}
        maxDate={new Date()}
        showMonthDropdown
        useShortMonthInDropdown
        renderCustomHeader={({ date: d, changeYear, changeMonth, decreaseMonth, increaseMonth }): JSX.Element => (
          <DatePickerHeader
            date={d}
            changeYear={changeYear}
            changeMonth={changeMonth}
            decreaseMonth={decreaseMonth}
            increaseMonth={increaseMonth}
          />
        )}
      />
      <CommonButtons asFooter>
        <Button shape='ghost' size='big' onClick={handleClose} translate>
          {t('front:global.cancel')}
        </Button>
        <Button shape='primary' size='big' onClick={handleConfirm} translate>
          {t('front:global.go')}
        </Button>
      </CommonButtons>
    </div>
  )
}

export default CustomDatePicker

// 9
import { ChangeEvent, Dispatch, MouseEvent, SetStateAction, useMemo } from 'react'
import styles, { cx } from 'styles'

import { useState } from 'hooks'

import { PageHandleIcon, TooltipIcon } from 'svgs'

interface SliderProps {
  currentPage: number
  totalPage: number
  tooltips?: string[]
  setPage: Dispatch<SetStateAction<number>> | ((value: number) => void)
  wrapperWidth: number
  scrollToTop: () => void
}

const Slider = ({
  currentPage,
  totalPage,
  tooltips,
  setPage,
  wrapperWidth,
  scrollToTop,
}: SliderProps): JSX.Element | null => {
  const [hover, setHover] = useState<{
    date?: string
    x?: number
  }>({})

  const sliderX = useMemo(() => currentPage - 1, [currentPage])

  const handleOnChange = (event: ChangeEvent<HTMLInputElement>): void => {
    const { value } = event.currentTarget
    setPage(Number(value) + 1)
  }

  const handleMouseOut = (): void => setHover({})

  const handleHover = (e: MouseEvent): void => {
    if (!tooltips) return

    const { x } = e.currentTarget.getBoundingClientRect()
    const hoverWidth = wrapperWidth / totalPage
    const hoveredPageNumber = parseInt(`${(e.clientX - x) / hoverWidth}`, 10)
    const date = tooltips[hoveredPageNumber]
    if (!date) return

    setHover({
      date,
      x: e.clientX - x,
    })
  }

// 10
  return (
    <div className={styles.sliderWrapper} onMouseMove={handleHover} onMouseOut={handleMouseOut} onBlur={handleMouseOut}>
      <input
        type='range'
        step={0}
        min={0}
        max={totalPage - 1}
        value={sliderX}
        onChange={handleOnChange}
        onMouseUp={scrollToTop}
      />
      <div
        className={cx(styles.fakeHandle, { [styles.hover]: hover.date })}
        style={{
          left: `${(wrapperWidth / totalPage) * sliderX}px`,
          width: `${wrapperWidth / totalPage}px``,
        }}
      >
        <PageHandleIcon />
      </div>
      {hover.date && (
        <div className={styles.hoverDate} style={{ left: hover.x }}>
          <p>{hover.date}</p>
          <TooltipIcon role='tooltip' />
        </div>
      )}
      <div className={styles.fakeTrack} />
    </div>
  )
}

export default Slider

// 11
export interface WalletDataCore {
  flatFee: string
  rateFee: string
  minAmount: string
  maxAmount: string
  validFrom: number
}

export interface FeeListItem extends WalletDataCore {
  blockchainName: string
  currency: string
}

export interface FeeListData {
  withdrawalFees: FeeListItem[]
}

export interface WithdrawBalanceData extends WalletDataCore {
  withdrawableAmount24h: string
}

export interface AddressData {
  address: string
  addressParams?: {
    destinationTag: string
  }
}

export interface WithdrawalParams {
  blockchainName?: string
  currency: string
  address: string
  addressParams?: {
    destinationTag: string
  }
  netAmount: string
  fee: string
  token: string
}

export interface WithdrawalSucessData {
  id: string
}

export interface WithdrawalErrorData {
  error: string
  errorDetails: {
    reason: string
    expiredAt: number
  }
}

// 12
/* eslint-disable camelcase */

export interface ZendeskArticle {
  id: number
  html_url: string
  created_at: string
  section_id: number
  title: string
  body: string
}

export interface ZendeskArticles {
  articles: ZendeskArticle[]
  count: number
  next_page: boolean
  page: number
  page_count: number
  per_page: number
  previous_page: boolean
  sort_by: string
  sort_order: string
}
```

1.  eslint & prettier의 중요성 : eslint & prettier 항상 적용해야한다. error나 warning이 절대 보이지 않게 해달라고 다시 한번 강요하셨다.
2.  README 작성 : README는 확인하는 사람이 폴더 구조를 생각할 수 있게 해주도록 프로젝트의 설계를 파악할 수 있게끔 작성한다.
3.  scss module 파일명 : example.module.scss와 같이 scss의 경우 파일명은 소문자로 작성하는 것이 좋다.
4.  공통 컴포넌트 : components 폴더 내부에 공통으로 쓰는 경우 컴포넌트는 common 폴더를 하나 만들어서 그 내부에 사용할 수도 있다. 이렇게 공통으로 쓰는 컴포넌트를 별도로 관리하여 다른 프로젝트 진행 시 common 폴더 자체를 복붙해서 템플릿처럼 사용할 수 있다.
5.  children과 outlet : 최근 react에서는 children을 대체하여 outlet을 사용하기도 한다.
6.  suspense : use suspense를 사용하여 spinner 구현 코드를 깔끔하게 작성할 수 있다. (참고 : https://ko.reactjs.org/docs/concurrent-mode-suspense.html)
7.  api의 instance화 : api는 src -> lib -> services 폴더 내부에 인스턴스로 만들어 사용한다.
8.  axios vs ky : axios는 ky와 다르게 time out을 잘 잡지 못한다.
9.  디바운스와 스로틀링 : 디바운스(Debounce)와 스로틀(Throttle)를 활용한다. 수영님이 추천해주신 디바운스 시간은 300을 추천하셨고 원래는 서버개발자랑 맞추어가는 것이 좋다고 한다. (참고 : https://www.zerocho.com/category/JavaScript/post/59a8e9cb15ac0000182794fa)
10. import, state 정리 : import할 때나 state부분에 용도 혹은 어디서 가져오냐를 구분하여 정리해두면 가독성이 좋아진다. import의 경우 예시로 라이브러리 -> 훅 or 타입 -> svg의 순서로 나누어 정리한다.
11. 중첩 구조분해할당 : 구조분해할당 사용 시 두번의 구조분해가 필요한 경우 한번에 해도 가독성이 괜찮다면 중첩하여 한번에 구조분해하여 코드의 길이를 줄이고 가독성을 좋게한다.
12. ts에서 선언식과 표현식 : 타입스크립트에서 함수 선언식이나 함수 표현식이나 타입추론이 달랐던 차이가 있었으나 버전이 업그레이드되면서 무관해졌다. (ex const Component (() => {}) / function Component() {})
13. state의 배열 : state의 값이 동적으로 들어가며 그 값이 array인 경우 초기값을 넣지 않는 것보다 빈 array로 넣어주는 것이 좋다.
14. query string의 object화 : axios나 fecth 사용 시 query string을 직접 만들어 사용하는 것이 아닌 object로 만들어 사용하는 것이 좋다.
15. api 환경변수 : api키를 노출시키지 않도록 환경 변수로 꼭 관리해주어야한다.
16. ts의 type과 interface : type과 Interface의 경우 a | b | c와 같은 나열의 경우 type, 확장이 필요한 경우 interface를 사용한다.

```ts
type AType = 'aa' | 'bbb' | 'ccc'

interface AInter {
  children?: ReactNode:
}

interface BInter extends AInter {
  ...
}

type BType = AType & | {}
```

17. 무한 스크롤 : react Intersection Observer로 무한 스크롤을 구현할 수 있다.

<br>

- **강의 내용**

1.  .env.copy 파일 : 오픈 소스는 api의 key값에 따라 사용량 체크하고는 하는데 이 key값은 노출되면 안된다. 이 key값을 안전하게 보관하기 위해 gitignore에 꼭 추가해주고 환경 변수로 관리해준다. process.env.~ 과 같이 가져다가 사용할 수 있다. ~부분의 접두사는 웹팩 설정에 필수인 부분이 있으니 확인해주어야한다.
2.  리코일의 리셋 기능 : 리코일의 기능 중 하나로 리셋 기능이 있다. 예를 들어 useState사용 시 리셋 기능이 하나 더 추가된 것이라고 볼 수 있다. (ex [a, setA, resetA])
3.  ul태그 : ul태그의 자식 태그 중 첫번째는 반드시 li가 와야한다. 아닌 경우 접근성에 위배된다.
4.  라우터 6버전의 슬래시 : 라우터 버전6의 경우 홈 path만 /로 넣어주고 나머지는 슬래시를 빼준다. 또한 404에러 페이지의 경우 path를 `*`로 설정하면 된다.
5.  Link와 NavLink 차이 : Link와 NavLink의 차이는 둘 다 페이지 이동에 사용하며 className에 isActive 유무가 차이점이다. isActive는 boolean값이 생성된다. 예시로 isActive를 사용하여 탭 GNB바에 활성화 된 탭을 스타일을 굵게 변경하거나 하는 경우 사용할 수 있다.
6.  useNavigate의 실무 사용 : 실무에서도 많이 사용하는 훅이다. navigate(0)을 사용하여 해당 페이지를 새로 불러올 수 있다. nextPage같은 변수를 상용하여 다음 페이지로 넘어가게 하거나 할 수 있다.
7.  비동기 함수의 클리어 처리 : 마운트 시 api로 받아온 값을 일정 시간마다 갱신하기 위해 setInterval함수를 사용하는 경우 언마운트시 clearInterval을 꼭 해주어야한다. setTimeout도 마찬가지이다. 또한 비동기 함수의 경우 클리어 처리가 필수이기때문에 미리 클리어까지 함께 사용하는 함수를 만들어 재사용하는 것이 좋다. 그러면 이 함수만 호출하여 사용할 수 있으므로 생산성과 가독성이 좋아진다.
8.  타입 모듈화 : interface 타입의 경우 services 폴더 -> types 폴더 -> ‘파일명’.d.ts 과 같은 파일 안에서 관리해준다. export하고 type/‘파일명’.d로 import하여 사용한다.
9.  리코일과 리덕스의 적용 범위 : 리코일을 전역으로 쓰는 것보다는 한 페이지에서 한정된 공간에서 사용하는 것을 추천해주셨다. 리코일은 가벼운 사이즈에 알맞고 리덕스는 큰 사이즈에 알맞다.
10. 리코일의 유니크한 key : 리코일의 key값은 중복되지 않도록 사용해야한다.
11. atom selector의 get과 set : atom의 selector를 활용하여 섞어서 사용할 수 있다.

```ts
export const endDateState = atom<TDateFilter>({
  key: "#exportExcel_endDateState",
  default: null,
});

export const errorState = atom({
  key: "#exportExcel_errorState",
  default: "",
});

export const disabledSelector = selector({
  key: "#exportExcel_disabledSelector",
  get: ({ get }) => {
    const error = get(errorState);
    const startDate = get(startDateState);
    const endDate = get(endDateState);

    if (!startDate || !endDate || error) return true;
    return false;
  },
});
```

12. 조건문 예외 우선 return : 조건문을 통해 실행되는 함수의 경우 조건이 아닌 경우를 상단에 작성하여 return시키는 패턴을 활용하면 가독성과 성능면에서 좋다.
13. css 우선 적용 : 비주얼과 관련된 경우 함수로 처리하기보다는 가능한 css에서 처리하는 것이 좋다. (ex transition, transition delay 등)
14. redux toolkit : redux toolkit을 사용하면 편리하게 모듈화 된 작업이 가능하다.
15. props drilling 피하기 : children & outlet을 사용하거나 상태관리 tool을 사용하여 피할 수 있다.
16. 다국어 지원 기능 : react-i18next 라이브러리를 설치하고 useTranslation를 활용하여 다국어 지원 기능을 구현할 수 있다.
17. 패키지 설치 후 오류 : 패키지 설치 후 서버를 재시작 하지 않는 경우 에러가 발생할 수 있다.

<br>

## # Takeaway

오늘은 피그마를 통해 그립컴퍼니의 개인프로젝트 과제에 기획서를 작성하였다. 오랜만에 기획서를 보니 퍼블리싱하던 시절이 생각났다.
디자인이 자유였고 기능에 대한 정리가 필요했기 때문에 피그마를 통해 기획서를 새로 작성하였다. 오랜만에 기획서를 작성하다보니 머리가 돌아가질 않았던 것 같다.
내일은 꼭 완성하고 프로젝트 초기 세팅까지 마무리해야겠다. 또한 오늘 강의 시간에는 게스트(?)한 분이 오셨다.
로켓런치 이준혁님의 동료이신 5년차 개발자 장수영님이 오셨다. 장수영님께 코드 리뷰를 받는 시간을 가졌는데 짧은 시간이었지만 정말 알찬 시간이었다.
장수영님이 설명해주신 것들 중에 이해가 가지 않는 부분들도 존재했지만 분명 짧은 시간에 많은 것을 배웠으며 공부할 수 있는 키워드들을 많이 알 수 있는 시간이었다.
또한 장수영님을 보고 느낀점은 내가 5년차 개발자가 된다면 저만큼 성장해야겠다는 목표를 세우게 된 것 같다.
장수영님의 코드 리뷰가 끝난 뒤 먼저 퇴장하셨는데 그 후 이준혁님이 말씀해주시기를 장수영님은 퇴근 후에도 계속해서 개발을 공부한다고 하셨다.
또 코드 작성 시 문제에 부딪히게 되면 우회하여 피해가는 경우가 있는데 그런 것이 아닌 정확히 알고 넘어가는 스타일이라고 하셨다.
참 배울 분이 많으신 선배 개발자셨다. 나도 5년차에는 물경력 쌓인 아무것도 모르는 가성비 나쁜 개발자가 아닌 5년차에 맞는 고급 개발자가 되고 싶다.
오늘 강의 시간은 정말 알찬 시간이었고 강의 시간마다 항상 강의 시간을 초과하는 열정을 보여주시며 또 참가자들의 발전을 위해 게스트까지 초대해주시며 정말 감사했다.
